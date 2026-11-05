---
title: "REACTIVE FORMS FOR BEGINNERS"
permalink: "/2018/08/24/reactive-forms-for-beginners/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-08-24"
---

{% raw %}
In Angular, there are two types of forms:  
— Template Driven Forms  
— Reactive Forms

If you are new to forms, understand these [**here**](https://angular.io/guide/forms). In this blog post, we will learn how to create custom validators for Angular Reactive Forms.

So, to start with, I assume that you have already created a project using **ng new.**Now, suppose we have created a reactive form using FormGroup.

```typescript
loginForm: FormGroup;
ngOnInit() 
	this.loginForm = new FormGroup({
		email: new FormControl(null),
		password: new FormControl(null),
		age: new FormControl(null)
	});
}
```

Let’s attach it to the template of the component using property binding, as follows.

```html
<form (ngSubmit)='loginUser()' [formGroup]='loginForm' novalidate class="form">
<input formControlName='email' type="text" class="form-control" placeholder="Enter Email" />
<br />
<input formControlName='password' type="password" class="form-control" placeholder="Enter Password" /> <br />
 <input formControlName='age' type="number" class="form-control" placeholder="Enter Age" />
<br />
<button [disabled]='loginForm.invalid' class="btn btn-default">Login</button>
 </form> 
```

This will display a reactive form like this.

![](/assets/img/9c642d-17615-1eannjt053hrn1ybni-fpcg.jpeg)

Till now, we did not use any validation in our form controls. Angular provides us with many validators like maxlength, required etc. To use them, do not forget to import Validators in the component class.

i**mport { FormGroup, FormControl, Validators } from ‘@angular/forms’;**

Suppose we use validation on the email and password, here’s how it is done.

```typescript
ngOnInit() {
 this.loginForm = new FormGroup({
      email: new FormControl(null, [Validators.required]),
      password: new FormControl(null, [Validators.required, Validators.maxLength(8)]),
     class: new FormControl(null)
     });
}
```

Inside **app.component.html**

```html
<input formControlName='email' type="text" class="form-control" placeholder="Enter Email" />
<div class="alert  alert-danger" *ngIf="loginForm.get('email').hasError('required') && loginForm.get('email').touched">
    Email is required
</div>
 <input formControlName='password' type="password" class="form-control" placeholder="Enter Password" />
 <div class="alert  alert-danger" *ngIf=" !loginForm.get('password').valid && loginForm.get('email').touched">
   Password is required and should less than or equal to 8 characters
 </div>


       
```

This displays:

![](/assets/img/69dbe9-bac78-1gjluzqthy_08wh2gfwiv3a.jpeg)

Now that we have applied validation to email and password, for class we want to create a validation for range such that the class should be from 1 to 12 only. In this case, we will have to write a custom validator as Angular doesn’t provide range validation.

So for that, we need to create a function that takes one input parameter of type AbstractControl and returns an object of key value pair in case the validation fails.

> function classValidator(control: AbstractControl) : {[key : string] : boolean} | null {  
> return null;  
> }

Here we have created a custom validator named classValidator where the user will be able to enter a class only if it’s in the given range. In case of failure of validation, it will return an object which contains key value pair.

In the component class,  
class: new FormControl(null, [classValidator])

On the Template, it goes like:

```html
<input formControlName='Class' type="number" class="form-control" placeholder="Enter Class" />
 <div class="alert  alert-danger" *ngIf="loginForm.get('class').dirty && loginForm.get('class').errors && loginForm.get(‘class’).errors.classRange ">
     Class should be in between 1 to 12 
 </div>
```

This will display:

![](/assets/img/89d08c-7d0ac-1xwdw6lf3gcnv_qel10thog.jpeg)

This is how Custom validators help us put validation to our form controls.
{% endraw %}
