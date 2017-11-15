# FamilySearch Web Components

[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/collection/fs-webcomponents/fs-elements)

FamilySearch web components is a library of [Polymer](https://www.polymer-project.org/1.0/)
elements that use the [FamilySearch API](https://familysearch.org/developers/)
to display data from the FamilySearch Family Tree.

Try out the [sample app](https://fs-wc-sample-app.herokuapp.com/) to see the
components in action.

## Current Status

The web components are in a beta state. The concept has been proven and the
architecture is sound but they need a bit a polishing. [Styles](https://github.com/fs-webcomponents/fs-elements/issues/1)
need to be standardized and an [error handling](https://github.com/fs-webcomponents/fs-elements/issues/2)
strategy needs to developed. Those two and other outstanding issues are listed 
in the [fs-elements issue tracker](https://github.com/fs-webcomponents/fs-elements/issues).

## Demos

The demos don't work well on the webcomponents.org catalog because the redirect
URI for OAuth is difficult to handle. Thus each element links to a version of 
their demo hosted on GitHub pages.

## Usage

_It is expected that you already know how to use Polymer. If not, please review
their tutorials._

First you need to configure the SDK client with an `<fs-client>` element. Without
it the components can't load any data from the API.

```html
<fs-client app-key="MY-APP-KEY" redirect-uri="/my/redirect/path" environment="production"></fs-client>
```

Then add a component that display some data.

```html
<fs-person-summary person-id="PPPP-PPP"></fs-person>
```

We recommend adding a `<fs-signin>` button to the page too so that the user can
login. The components will automatically update their state after the user signs
in. In this case `<fs-person-summary>` will automatically load the person and
display the profile summary after the user signs in. It will also automatically
clear the data when the user signs out.

View the source code for the component demos to see how easy it is to use them.

## Creating Your Own Element

`<fs-client>` is the foundation of FamilySearch web components because it manages
access to the SDK. Without it your element can't request data from the API.

We recommend setting the `debounceDuplicates` property to true on `<fs-client>`.
This allows multiple elements to request data from the same resource while only
having one HTTP request sent to the API by the SDK.

Review the code for one of the existing elements to see how you might write your
own element that uses `<fs-client>` to get data from the FamilySearch API.
`<fs-person-chip>` is a good example of a simple component that relies on 
`<fs-person-mixin>` to do most of it's heavy lifting. `<fs-person-portrait>` is
a little more complex but is used by most other components that display people.
`<fs-pedigree>`, `<fs-person-families>`, and `<fs-add-person>` are complex in 
their processing and displaying of data.