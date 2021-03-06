## This seems to be fixed:

Thanks to [yehiaazanki](https://stackoverflow.com/users/3193819/yehiaazanki) on [Stack Overflow](https://stackoverflow.com/questions/68200189/using-fontawesome-5-15-0-with-primefaces-8-0) I found out this seems to be fixed. The only change (as you can see in one of the last commits) was to set `primefaces.FONT_AWESOME` to `true` (as opposed to what the docs say).

The [FontAwesome bars icon](https://fontawesome.com/icons/bars?style=solid) is showing again and I tested with the [500px icon](https://fontawesome.com/v5.15/icons/500px?style=brands) in the menu, which is a FontAwesome 5.0.0 icon.

## Original problem:

This project was created from the archetype "wildfly-jakartaee-webapp-archetype" (from "org.wildfly.archetype").

Then, the following dependencies were added to the POM:

```xml
<dependency>
	<groupId>org.primefaces</groupId>
	<artifactId>primefaces</artifactId>
	<version>8.0</version>
</dependency>
<dependency>
	<groupId>com.github.adminfaces</groupId>
	<artifactId>admin-template</artifactId>
	<version>1.1.0</version>
</dependency>
<dependency>
     <groupId>org.webjars</groupId>
     <artifactId>font-awesome</artifactId>
     <version>5.13.0</version>
</dependency>
```

Then, src/main/webapp/WEB-INF/templates/template.xhtml was created with a simple AdminFaces template. Following the instructions from [PrimeFaces Documentation](https://primefaces.github.io/primefaces/8_0/#/core/fonticons), `<h:outputStylesheet />` tags were added to the head:

```xhtml
<ui:define name="head">
	<h:outputStylesheet library="webjars" name="font-awesome/5.13.0/css/all-jsf.css" />
	<h:outputStylesheet library="webjars" name="font-awesome/5.13.0/css/v4-shims-jsf.css" />
    <title>AdminFaces / FontAwesome Example</title>
</ui:define>
```

Then, src/main/webapp/index.xhtml was created to exercise the template.

Then, a minimal web.xml was added to the project, again to follow the instructions from [PrimeFaces Documentation](https://primefaces.github.io/primefaces/8_0/#/core/fonticons) to set `primefaces.FONT_AWESOME` to `false`.

When deployed on WildFly 19 (but I had this problem in WildFly 17 as well) the [FontAwesome bars icon](https://fontawesome.com/icons/bars?style=solid) from the menu is replaced by a square, i.e., it doesn't work. See the README-screenshot.png file.

This project is an example in order to try to fix this. I want to upgrade to FontAwesome 5 in [another project](https://github.com/dwws-ufes/marvin) that uses PrimeFaces and AdminFaces. I appreciate any help, thanks!
