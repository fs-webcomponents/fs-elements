# FamilySearch Web Components

[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://beta.webcomponents.org/collection/fs-webcomponents/fs-elements)

FamilySearch web components are a library of [Polymer](https://www.polymer-project.org/1.0/)
elements that use the [FamilySearch API](https://familysearch.org/developers/)
to display data from the FamilySearch Family Tree.

Try out the [sample app](https://fs-wc-sample-app.herokuapp.com/) to see the
components in action.

## Elements

* [fs-client](https://github.com/fs-webcomponents/fs-client) - Configure and manage access to the JS SDK client.
* [fs-behavior](https://github.com/fs-webcomponents/fs-behavior) - A behavior that makes it easy for elements to access the client.
* [fs-person-behavior](https://github.com/fs-webcomponents/fs-person-behavior) - A behavior that makes it easy for elements to request person data.
* [fs-signin](https://github.com/fs-webcomponents/fs-signin) - Manage authentication state with a Sign In / Sign Out button.
* [fs-person-portrait](https://github.com/fs-webcomponents/fs-person-portrait) - Display a person's portrait.
* [fs-person-chip](https://github.com/fs-webcomponents/fs-person-chip) - Display a person's portrait, name, lifespan, and ID.
* [fs-person-facts](https://github.com/fs-webcomponents/fs-person-facts) - List a person's facts.
* [fs-person-families](https://github.com/fs-webcomponents/fs-person-families) - List a person's families.
* [fs-person-sources](https://github.com/fs-webcomponents/fs-person-sources) - List a person's sources.
* [fs-person-summary](https://github.com/fs-webcomponents/fs-person-summary) - Show the summary of a person.
* [fs-pedigree](https://github.com/fs-webcomponents/fs-pedigree) - Show a person's pedigree.

## Docs

The element docs are published to individual gh-pages branches for each element.

The element docs are also published on the new [webcomponents.org](https://beta.webcomponents.org/) 
catalog. There we've published a [collection](https://beta.webcomponents.org/collection/fs-webcomponents/fs-elements)
of the FamilySearch elements. However the demos likely won't work because of
technical issues involving redirect URIs for OAuth.

## Usage

_It is expected that you already know how to use Polymer. If not, please review
their tutorials._

First configure the SDK client with and `<fs-client>` element.

```html
<fs-client app-key="MY-APP-KEY" redirect-uri="/my/redirect/path"></fs-client>
```

We recommend adding a `<fs-signin>` button to the page too so that the user can
login.

## Creating Your Own Element

`<fs-client>` is the foundation of FamilySearch web components because it manages
access to the SDK. Without your element can't request data from the API.

We recommend setting the `debounceDuplicates` property to true on `<fs-client>`.
This allows multiple elements to request data from the same resource while only
having one HTTP request sent to the API by the SDK.

Review the code for one of the existing elements to see how you might write your
own element that uses `<fs-client>` to get data from the FamilySearch API.
`<fs-person-chip>` is a good example of a simple component that relies on 
`FSPersonBehavior` to do most of it's heavy lifting. `<fs-person-portrait>` is
a little more complex but is used by most other components that display people.
`<fs-pedigree>` and `<fs-person-families>` are complex in their processing and
displaying of data.

## Status

The web components are in a beta state. The concept has been proven and the
architecture is sound but they need a bit a polishing. Styles are not consistent
and it wasn't until recently that we decided to stick with Material Design via
Polymer [paper elements](https://beta.webcomponents.org/collection/PolymerElements/paper-elements).
