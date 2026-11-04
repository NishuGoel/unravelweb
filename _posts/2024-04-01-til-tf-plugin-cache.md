---
title: "til: TF plugin cache"
permalink: "/2024/04/01/til-tf-plugin-cache/"
tags: ["Node.js", "Terraform", "Uncategorized", "javascript", "terraform"]
layout: "post"
date: "2024-04-01"
---

{% raw %}
Writing a tool at work to move our infrastructure setup to a more declarative approach. To do so, I run terraform inside AWS Lambda (will write about this some time), every time a configuration needs to be applied.

I use the terraform `import` feature to copy configurations from test accounts, and need to do so for all dependencies of one resource being “imported”, to avoid missing configs.   
Since this happens iteratively, running `terraform init` every run to get the providers installed was a bad idea since 1) redundant 2) less efficient.

***Plugin Cache Dir***

`terraform init` was maintaining separate copies of the plugins and were being downloaded for each configuration.

Terraform optionally allows the use of a local directory as a shared plugin cache which can be used as the central plugins directory, thus avoiding downloading the plugins every time.

To enable the plugin cache, use the `plugin_cache_dir` setting in the CLI configuration file `.terraformrc`. For example:

```
plugin_cache_dir = "$HOME/.terraform.d/plugin-cache"
```

The plugin-cache directory needs to be created already since the `init` command will not create it if not found. Terraform will then use. the installed plugins from this directory if present already, and install in the plugin cache if the directory is empty

OR

```
terraform init -plugin-dir=$HOME/.terraform.d/plugin-cache
```

***FileSystem Mirror configuration***

We could also use a *filesystem mirror* method to explicitly install plugins using a local directory with the option to include/exclude specific providers.

```
provider_installation {
  filesystem_mirror {
    path    = "/usr/terraform.d/providers"
    include = ["example.com/*/*"]
  }
  direct {
    exclude = ["example.com/*/*"]
  }
}
```

Both worked well for the above case, with plugin cache being a straightforward approach 👍
{% endraw %}
