#1.0.0

## Breaking Changes
- new dependency: `angular-formly@3.0.*`
- `<formly-form>` attribute `result` changed to `model`. See example below:

```html
  <formly-form model="formData" fields="formFields"></formly-form"
```

- `lx-text-field` shortened to `lx-text`
- `lx-radio-buttons` shortened to `lx-radio`
- removed `lx-subhead` in favor of new feature: 'wrappers'
- `class` properties renamed `className` to avoid need for quotes
- file structure changed: './src/modules/*'
- demo added './demo/app'
- all template related form-fields put into [templateOptions](https://github.com/formly-js/angular-formly#templateoptions-). See the example below:

```javascript
{
  'key': 'someKey',
  'templateOptions': {
    'type': 'text', // html input type values [text, email, password, url, number]
    'label': 'Some Label', // acts as a placeholder & label
    'fixedLabel': false, // [default = false (float label), true = fixed label]
    /* all template related fields here */
  },
  validators: {},
  modelOptions: {}
}
```

## Features
- new [site with improved docs](https://github.com/formly-js/angular-formly-templates-lumx)
- see [changes to angular-formly](https://github.com/formly-js/angular-formly/blob/master/CHANGELOG.md)
- add ng-directives using `bound` on [ngModelAttrs](https://github.com/formly-js/angular-formly#ngmodelattrs-object)
- other directives can be added to templates using `unbound` on ngModelAttrs
- ngModelAttrs can be manipulated using `expressionProperties`. See example below:

```javascript
{
  'key': 'item1',
  'type': 'lx-checkbox',
  'tempateOptions': {
    'value': false
  }
},
{
  'key': 'item2',
  'type': 'lx-text',
  'ngModelAttrs': {
    'bound': {
      /* adds ng-directive to field input */
      'ng-pattern': /[A-Za-z]/,
      'ng-disabled': false,
      'ng-maxlength': 10,
      'ng-required': true
    },
    'unbound': {
       /* add other/custom directives here */
    }
  },
  expressionProperties: {
    'ngModelAttrs.bound['ng-disabled']: 'model.item1'
  }
}
```


## In Progress
- `lx-wrapper-*`. Wrap data around your template for greater style control.
- `lx-flex` (flexbox feature)

## Inner changes
- Gulpfile to easily generate templates from fields
- Many ng-directives removed from templates in favor of ngModelAttrs
- Some custom select attributes removed
- `aria-labeledby` changed to `aria-describedby`
- `ngModel[options.key || $index]` simplified to `ngModel[options.key]`
- `formly-name-