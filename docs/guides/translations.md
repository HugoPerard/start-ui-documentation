# Translations

## Setup the i18n Ally extension

We recommended using the [i18n Ally](https://marketplace.visualstudio.com/items?itemName=lokalise.i18n-ally) plugin for VS Code for translations management.

Create or edit the `.vscode/settings.json` file with the following settings:

```json
{
  "i18n-ally.localesPaths": ["src/locales"],
  "i18n-ally.keystyle": "nested",
  "i18n-ally.enabledFrameworks": ["general", "react", "i18next"],
  "i18n-ally.namespace": true,
  "i18n-ally.defaultNamespace": "common",
  "i18n-ally.extract.autoDetect": true,
  "i18n-ally.keysInUse": ["common.languages.*"]
}
```

## Guidelines for translations

- Use namespaces `t('namespace:translationKey')` and nesting `t('namespace:this.is.nested')`.

```js
// Example for translations available in account.json
t("account:data.firstname.label");
```

- For fields and data translations use a `data` object.

```json
// account.json
{
  "data": {
    "firstname": {
      "label": "First Name",
      "required": "First Name is required"
    }
  }
}
```

```js
// React
t("account:data.firstname.label");
t("account:data.firstname.required");
```

- For user feedbacks, use a `feedbacks` object with `actionSuccess` & `actionError` keys containing each `title` and `description` (optional).

```json
// account.json
{
  "resetPassword": {
    "feedbacks": {
      "confirmSuccess": {
        "title": "Your password has been reset",
        "description": "You can now login"
      },
      "confirmError": {
        "title": "Reset password failed"
      }
    }
  }
}
```

```js
// React
t("account:resetPassword.feedbacks.updateSuccess.title");
t("account:resetPassword.feedbacks.updateSuccess.description");
t("account:resetPassword.feedbacks.updateError.title");
```

- For user actions, use an `actions` object.

```json
// account.json
{
  "resetPassword": {
    "actions": {
      "send": "Send Email",
      "reset": "Reset Password"
    }
  }
}
```

```js
// React
t("account:resetPassword.actions.send");
t("account:resetPassword.actions.reset");
```

- Use the common workspace only for VERY generic translations. By default, use specific namespaces to allow easy update on large code base without unwanted side-effects.
