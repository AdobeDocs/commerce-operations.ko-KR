---
title: '[!DNL Upgrade Compatibility Tool]'
description: ' [!DNL Upgrade Compatibility Tool] '
source-git-commit: a13b0ea5aa109ce2f5d33e0966b194d64bad5d0c
workflow-type: tm+mt
source-wordcount: '3782'
ht-degree: 4%

---


# [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

[!DNL Upgrade Compatibility Tool]

Error messages are categorized by level (critical issues, errors, and warnings) and type (core code, custom code, and GraphQL schemas). Each type contains the following information:

- ****
- ****
- ****

## Critical issues

### Core code

These errors are reported when some of the core files are missing or do not match the original.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 2001 | Core file was not found | `composer install` |
| 2002 | Core file was modified | `composer install` |
| 2003 | Composer dependency is not installed | Missing composer dependency may potentially result in issues. `composer require package_name` |
| 2005 | Core folder was not found | `composer install` |

{style=&quot;table-layout:auto&quot;}

### Custom code

Critical errors are raised when the custom code is referencing entities that are not present in the target Adobe Commerce version. These errors are also reported when critical coding standards have been broken.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 1110 | Instantiating non-existent Adobe Commerce class/interface | `@api` Instantiating non-existent Adobe Commerce class/interface. |
| 1111 | Extending from non-existent Adobe Commerce class | The extended class is no longer present in the codebase. Inheritance is not recommended way of extending Adobe Commerce functionality. `@api` |
| 1112 | Importing non-existent Adobe Commerce class | `@api` |
| 1113 | Loading non-existent Adobe Commerce class | `@api` |
| 1114 | Using non-existent Adobe Commerce class | `@api` |
| 1214 | Using non-existent Adobe Commerce constant | Consider introducing and using a private constant of the required value within the custom code instead. |
| 1215 | Overriding non-existent Adobe Commerce constant | Consider introducing and using a private constant of the required value within the custom code instead. |
| 1216 | Assignation of non-existent Adobe Commerce constant | Consider introducing and using a private constant of the required value within the custom code instead. |
| 1312 | Imported non-existent Adobe Commerce interface | Consider removing the inheritance or replacing it with the interface introduced in the scope of the customization. |
| 1314 | Used non-existent Adobe Commerce interface | Consider removing the inheritance or replacing it with the interface introduced in the scope of the customization. |
| 1317 | Inherited non-existent Adobe Commerce interface | Consider removing the inheritance or replacing it with the interface introduced in the scope of the customization. |
| 1318 | Implemented non-existent Adobe Commerce interface | Consider removing the inheritance or replacing it with the interface introduced in the scope of the customization. |
| 1410 | Call non-existent Adobe Commerce method | `@api` |
| 1514 | Using non-existent Adobe Commerce property | `@api` |
| 1515 | Overriding non-existent Adobe Commerce property | `@api` |
| 1516 | Assignation of non-existent Adobe Commerce property | `@api` Update the property access level to private if it can be used within a single class only. |
| 5002 | The opening PHP tag must be the first content in the file | Ensure there is no content in the file before the PHP opening tag. |
| 5003 | Function has been deprecated | Use a replacement suggested in the error message. If the message does not suggest a replacement, a close review is needed to select an alternative function or implementation. |
| 5005 | PHP syntax error | The code must be updated to comply with the PHP syntax standards. |
| 5072 | Possible Magento 2 design violation. Detected a typical Magento 1.x construction | Update construction to Magento 2 standards. |
| 5076 | Cannot use in namespace as it is reserved since PHP 7 | Replace the reserved word in the namespace with a non-reserved keyword. |
| 5077 | Cannot use as class name as it is reserved since PHP 7 | Replace the reserved class name with a non-reserved name. |

{style=&quot;table-layout:auto&quot;}

### GraphQL Schema

GraphQL Schema critical issues are raised if the schema items are not present in the target version.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 3101 | Type was removed | List all queries that are referencing this field. Check if these queries are used by the customization implementation. Update the client code to handle the changed query interface. |
| 3102 | Type removed from union | If the union type is used in the GraphQL request constructing or response processing implementation it may need to be updated. |
| 3103 | Field removed | Check if the field is referenced in the customization codebase. Adjust the implementation to correctly handle the new field type. |
| 3105 | Implemented interface removed | Check if the type implementing the removed interface is used in the customization. The implementation may need to be updated if it is relying on the removed interface. |
| 3106 | Value removed from enum | If the removed enum value is used in the GraphQL request constructing or response processing implementation it may need to be updated. |
| 3107 | Argument removed | Check if the field is used in the customization codebase. Remove the argument for this field. |
| 3109 | Directive removed | Check if the directive is used in the customization codebase. Adjust the implementation to remove the reference to the directive. |
| 3110 | Directive argument removed | Check if the directive is used in the customization codebase. Remove the directive argument. |
| 3111 | Directive repeatable removed | Check if the directive is used in the customization codebase. Adjust the implementation to handle the interface changes. |
| 3112 | Directive location removed | Check if the directive is used in the customization codebase. Adjust the implementation to handle the interface changes. |
| 3201 | Type changed kind | List all queries that are referencing this field. Check if these queries are used by the customization implementation. Update the client code to handle the changed query interface. |
| 3203 | Field changed kind | Check if the field is referenced in the customization codebase. Adjust the implementation to correctly handle the new field type. |
| 3207 | Argument changed kind | Check if the field is used in the customization codebase. Update the argument type for this field. |
| 3303 | Required input field added | The field should be added to the request if the query including this field is used for the customization. |
| 3307 | Required argument added | Check if the field is used in the customization codebase. The new required argument should be specified when using the field. |
| 3310 | Required directive argument added | Check if the directive is used in the customization codebase. Add the directive argument. |

{style=&quot;table-layout:auto&quot;}

## Errors

### Custom code

`@api` The preserved behavior of such entry points is not guaranteed. `@api` The functionality that is based on non-API Adobe Commerce code should be tested after the upgrade. These errors are also reported when major coding standards have been broken.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 1104 | Using non-API class that is inheriting API interface | `@api` `@api` Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1121 | Extending from non-Adobe Commerce API class | The extended class is no longer present in the codebase. Inheritance is not recommended way of extending Adobe Commerce functionality. `@api` |
| 1122 | Importing non-Adobe Commerce API class | The extended class is no longer present in the codebase. `@api` Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1123 | Loading non-Adobe Commerce API class | The extended class is no longer present in the codebase. `@api` Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1124 | Using non-Adobe Commerce API class | The extended class is no longer present in the codebase. `@api` Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1224 | Using non-Adobe Commerce API constant | `@api` Consider introducing and using a private constant of the required value within the custom code instead. |
| 1225 | Overriding non-Adobe Commerce API constant | `@api` Consider introducing and using a private constant of the required value within the custom code instead. |
| 1226 | Assignation of non-Adobe Commerce API constant | `@api` Consider introducing and using a private constant of the required value within the custom code instead. |
| 1322 | Imported non-Adobe Commerce API interface | `@api` `@api` |
| 1324 | Used non-Adobe Commerce API interface | `@api` `@api` |
| 1327 | Inherited non-Adobe Commerce API interface | `@api` Consider introducing and using a private constant of the required value within the custom code instead. |
| 1328 | Implemented non-Adobe Commerce API interface | `@api` `@api` |
| 1420 | Instantiating non-Adobe Commerce API class/interface | `@api` `@api` Otherwise, the functionality relying on this implementation should be tested after the upgrade. Also, the recommended way of retrieving an instance of the class is using DI. Consider using a factory if a new instance of the class is required. |
| 1428 | Possible dependency on implementation details. | `@api` `@api` Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1429 | Call non-Adobe Commerce API methods | `@api` Even if the interface of the method is not updated in the new version, its behaviour or output can be different. Consider relying on an interface method. Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1449 | Call to non-interface method (that is present in implementation) | Methods that are not declared in the interface may be changed. Consider relying on an interface method. Otherwise, the functionality relying on this implementation should be tested after the upgrade. |
| 1524 | Using non-Adobe Commerce API property | `@api` Consider relying on the API interface method instead. |
| 1525 | Overriding non-Adobe Commerce API property | `@api` Consider relying on the API interface method instead. |
| 1526 | Assignation of non-Adobe Commerce API property | `@api` Consider relying on the API interface method instead. |
| 5004 | Function without argument has been deprecated | Pass the input to validate as the first argument of the function. |
| 5007 | The use of certain functions is discouraged | Avoid using these functions. |
| 5009 | Template directives may not invoke methods. Only scalar array access is allowed | Remove method invocations from the template. |
| 5010 | `@vars` | Fix invalid JSON. |
| 5011 | `@vars` | Fix invalid label. |
| 5012 | `@vars` | Add missing variable to @vars comment block. |
| 5013 | Avoid using self-closing tag with non-void html element | Use close tag instead. |
| 5014 | `"active"` | The list of active modules is defined in deployment configuration. |
| 5015 | `<param>` | `<argument name="..." xsi:type="...">` |
| 5016 | `<instance>` | `<argument name="..." xsi:type="object">` |
| 5017 | `<array>` | `<argument name="..." xsi:type="array">` |
| 5018 | `<item key="...">` | `<item name="..." xsi:type="...">` |
| 5019 | `<value>` | Instead, provide the actual value as a text literal. |
| 5020 | `<supported_blocks>` | `<supported_containers>` |
| 5021 | `<block_name>` | `<container_name>` |
| 5022 | Factory name detected | Widget type should not begin with /. |
| 5023 | Obsolete ACL structure detected in line | Check lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Obsolete menu structure detected in line | Check app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Obsolete system configuration structure detected in file | Check app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | `"text/javascript"` | Use only public members. |
| 5028 | `Block` | Use only public members. |
| 5031 | Contains obsolete method | `getConnection()` |
| 5042 | Incorrect format of PHP class reference | Check that class is referenced using only camelCased letters, numbers, and no leading slash. |
| 5043 | Incorrect format of module reference | Check that module is referenced using only letters, numbers, underscores, and no leading slash. |
| 5044 | `Zend_Db_Select` | `\Magento\Framework\DB\Select` |
| 5045 | `Zend_Db_Adapter_Pdo_Mysql` | `\Magento\Framework\DB\Adapter\Pdo\Mysql` |
| 5046 | `Magento\Framework\Serialize\Serializer\Serialize` | `Magento\Framework\Serialize\SerializerInterface` |
| 5047 | `ArrayObject` | `ArrayObject` |
| 5048 | `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` | `ArrayObject` |
| 5050 | The block being referenced is removed | Remove reference to block. |
| 5051 | `output="toHtml"` | `output="1"` |
| 5052 | `\Magento\Framework\View\Element\Text\ListText` | `\Magento\Framework\View\Element\Text\ListText` |
| 5053 | `<action>` | `<action>` |
| 5054 | `helper``/` | `/` |
| 5055 | `helper``::` | `::` |
| 5056 | Install scripts are obsolete | Use declarative schema approach in module\&#39;s etc/db_schema.xml file. |
| 5057 | InstallSchema scripts are obsolete | Use declarative schema approach in module\&#39;s etc/db_schema.xml file. |
| 5058 | InstallData scripts are obsolete | Use data patches approach in module\&#39;s Setup/Patch/Data dir. |
| 5059 | Install scripts are obsolete | Create a class InstallData in the module\&#39;s Setup folder. |
| 5060 | Upgrade scripts are obsolete | Use declarative schema approach in module\&#39;s etc/db_schema.xml file. |
| 5061 | UpgradeSchema scripts are obsolete | Use declarative schema approach in module\&#39;s etc/db_schema.xml file. |
| 5062 | UpgradeData scripts are obsolete | Use data patches approach in module\&#39;s Setup/Patch/Data dir. |
| 5063 | Upgrade scripts are obsolete | Use data patches approach in the module\&#39;s Setup/Patch/Data dir. |
| 5064 | Recurring scripts are obsolete | Create class Recurring in the module\&#39;s Setup folder. |
| 5065 | &#39;data&#39; is in an invalid directory | Create a data patch within module&#39;s Setup/Patch/Data folder for data upgrades or use declarative schema approach in module&#39;s etc/db_schema.xml file for schema changes. |
| 5066 | &#39;sql&#39; is in an invalid directory | Create a data patch within module&#39;s Setup/Patch/Data folder for data upgrades or use declarative schema approach in module&#39;s etc/db_schema.xml file for schema changes. |
| 5067 | Nodes identified by XPath are obsolete | Obsolete XML pointed out in the error should be updated. Follow the suggestions from the error message. |
| 5068 | `{{htmlescape}}` | `{{var}}` |
| 5069 | `{{escapehtml}}` | `{{var}}` |
| 5070 | `getChildHtml()` | `getChildHtml()` |
| 5071 | `getChildHtml()` | `getChildHtml()` |
| 5073 | Legacy table names with slash must be fixed to direct table names | Use direct table name instead. |
| 5075 | Application modules should not use classes from test modules | Remove usage of classes from test modules. |
| 5078 | Class must be requested in constructor, otherwise compiler will not be able to find and generate these classes | Add class to constructor. |
| 5079 | Use of var class variables is discouraged | Avoid using &#39;var&#39; to declare class variable. |
| 5080 | Possible raw SQL statement detected | Use repositories or data patches instead. |
| 5081 | The use of helpers in templates is discouraged | Use ViewModel instead. |
| 5082 | The use of $this in templates is deprecated | Use $block instead. |
| 5083 | Constants are not allowed as the first argument of translation function | Use string literal instead. |
| 5085 | The use of certain functions is discouraged | Use the alternative function advised on the message instead. |
| 5087 | PHP cross-version compatibility issue | [](https://www.php.net/manual/en/migration81.php) |
| 5088 | Optional parameters found after required ones | Move required parameters after optional ones. |
| 5089 | `final private` | `final private``private` |
| 5090 | `__set_state``static` | `__set_state``static` |
| 5091 | `__toString()``Stringable` | `Stringable``__toString()` |
| 5092 | `is_resource()` | `is_resource()``instanceof` |
| 6001 | `jQuery.andSelf()` | `jQuery.addBack()` |
| 6002 | `$.bind``$.unbind` | `$.on``$.off` |
| 6003 | jQuery method to subscribe to event is deprecated and shouldn&#39;t be used | `.on("event name", fn)` |
| 6003 | jQuery method to trigger event is deprecated and shouldn&#39;t be used | `.trigger("event name")` |
| 6004 | `$.delegate``$.undelegate` | `$.on``$.off` |
| 6005 | `jQuery.load()``jQuery.unload()``jQuery.error()` | `.on("load", fn)``.on("unload", fn)``.on("error", fn)` |
| 6006 | `jQuery.size()` | `jQuery.length` |
| 6007 | `jQuery.trim` | `String.prototype.trim` |
| 6008 | `addButton``addContextToolbar``addMenuItem``addSidebar``file_browser_callback``insert_button_items` | Update code to be compatible with tinymce5. |
| 6009 | `jQuery.isFunction()` | [] |
| 6009 | `jQuery.type()` | [] |
| 6009 | `jQuery.isArray()` | Use the native Array.isArray method instead. |
| 6009 | `jQuery.parseJSON()` | To parse JSON strings, use the native JSON.parse method instead. |
| 6010 | `jQuery.expr[":"]``jQuery.expr.filters` | Use jQuery.expr.pseudos instead. |

{style=&quot;table-layout:auto&quot;}

## Warnings

### Core code

These warnings are reported when there are minor inconsistencies in the core codebase.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 2004 | Composer dependency version mismatch | Issue indicates that Composer dependency version in etalon and actual project is different. `composer update <package_name>` |

{style=&quot;table-layout:auto&quot;}

### Custom code

Custom code warnings are raised when the references to deprecated code are detected. Such references should be replaced with the supported extension points. `@see` These errors are also reported when minor coding standards have been broken.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 1131 | ``@deprecated`` | The extended class will be removed in upcoming versions. Inheritance is not recommended way of extending Adobe Commerce functionality. `@api` |
| 1132 | `@deprecated` | The extended class will be removed in upcoming versions. `@api` |
| 1133 | `@deprecated` | The extended class will be removed in upcoming versions. `@api` |
| 1134 | `@deprecated` | The extended class will be removed in upcoming versions. `@api` |
| 1234 | `@deprecated` | The deprecated constant will be removed in upcoming versions. `@api` |
| 1235 | `@deprecated` | The deprecated constant will be removed in upcoming versions. `@api` |
| 1236 | `@deprecated` | The deprecated constant will be removed in upcoming versions. `@api` |
| 1332 | `@deprecated` | The deprecated interface will be removed in upcoming versions. `@api` |
| 1334 | `@deprecated` | The deprecated interface will be removed in upcoming versions. `@api` |
| 1337 | `@deprecated` | The deprecated interface will be removed in upcoming versions. `@api` |
| 1338 | `@deprecated` | The deprecated interface will be removed in upcoming versions. `@api` |
| 1430 | Call not declared dataobject method | The magic methods that are not declared may be changed. Consider relying on interface methods instead. |
| 1439 | `@deprecated` | The deprecated method will be removed in upcoming versions. Consider relying on methods declared in API interfaces instead. |
| 1440 | Method signature mismatch | A call or override of core method is detected with parameters, arguments or return type that does not match the method signature. |
| 1534 | `@deprecated` | The deprecated method will be removed in upcoming versions. Consider relying on methods declared in API interfaces instead. |
| 1535 | `@deprecated` | The deprecated property will be removed in upcoming versions. Consider relying on methods declared in API interfaces or using a private property within your implementation instead. |
| 1536 | `@deprecated` | The deprecated method will be removed in upcoming versions. Consider relying on methods declared in API interfaces instead. |
| 5006 | Proxies and interceptors MUST never be explicitly requested in constructors | The original class should be declared as a type of the constructor parameter. The Interceptor/Proxy class will be passed by the framework dependency injection implementation. |
| 5074 | `getResource()` | Use a repository instead. |
| 5086 | Visibility is not declared on a constant | Declare the visibility on all constants. |

{style=&quot;table-layout:auto&quot;}

### GraphQL Schema

GraphQL Schema warnings are raised when the additional items are added to the schema in the new version. It is recommended to review the implementation to see if they should be used for requests.

| Error code | Error description | Suggested action |
| --- | --- | --- |
| 3206 | Argument default value changed | If the query is used in the customization the argument value may have to be specified explicitly. |
| 3302 | Type added to union | The type was added to the union. Check the implementation processing the result of the query returning this union type and ensure it is able to handle the added type. |
| 3304 | Optional input field added | Optional input field added. Check the implementation to ensure. |
| 3305 | Implemented interface added | The field can accept/provide more information that can be considered in the implementation. |
| 3306 | Value added to enum | A value was added to an enum. If clients contain a switch statement on the enum&#39;s value and do not include a default case, this change might cause unexpected behavior. |
| 3308 | Optional argument added | If the query is using a new argument in the customization it may need to be added to the request. |

{style=&quot;table-layout:auto&quot;}
