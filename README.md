# Arabic Translations for React-Admin

Arabic translations for [React-Admin](https://github.com/marmelab/react-admin), the frontend framework for building admin applications on top of REST/GraphQL services.

[![react-admin-demo](https://marmelab.com/react-admin/img/react-admin-demo-still.png)](https://vimeo.com/268958716)

## Installation

```sh
npm install --save ra-language-arabic
```

## Usage

```js
import ArabicMessages from 'ra-language-arabic';

const messages = {
    'ar': ArabicMessages,
};

const i18nProvider = locale => messages[locale];

<Admin locale="ar" i18nProvider={i18nProvider}>
  ...
</Admin>
```

## RTL
Material UI is already supprting RTL, so we can add its support to react admin using these 2 steps:

1. Change **dir** property to **rtl** in your root elements (like body). You can also connect this property to redux.
2. Define a theme and set **direction** to **rtl**.

```javascript
import { createMuiTheme } from '@material-ui/core/styles';

const theme = createMuiTheme({
  direction: 'rtl',
});

const App = () => (
    <Admin theme={theme}>
        // ...
    </Admin>
);
```

*public/index.html*

```html
<body>
<noscript>
  You need to enable JavaScript to run this app.
</noscript>
<div id="root" dir="rtl"></div>
</body>
```

3. Add jss-rtl.

You need this JSS plugin to flip the styles: jss-rtl.
```javascript
npm install jss-rtl
```
Having installed the plugin in your project, Material-UI components still require it to be loaded by the jss instance, as described below. Internally, withStyles is using this JSS plugin when direction: 'rtl' is set on the theme. Head to the plugin README to learn more about it.

Once you have created a new JSS instance with the plugin, you need to make it available to all the components in the component tree. The StylesProvider component enables this:

```javascript
import { create } from 'jss';
import rtl from 'jss-rtl';
import { StylesProvider, jssPreset } from '@material-ui/core/styles';

// Configure JSS
const jss = create({ plugins: [...jssPreset().plugins, rtl()] });

function RTL(props) {
  return (
    <StylesProvider jss={jss}>
      {props.children}
    </StylesProvider>
  );
}
```



## License

This translation is licensed under the [BSD Licence](LICENSE), and sponsored by [Vahid Kheradmand](https://developerium.com).
