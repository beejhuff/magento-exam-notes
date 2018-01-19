### 1. Which method is used for translating strings, and on which types of objects is it generally available?

The magic method __() is used for translating strings, available to Models, Blocks, Helpers and also in templates.
The method retrieves three translation types from the following places.

- Module Translation:	CSV in /app/locale
- Theme Translation:	CSV in /app/design/{area}/{package}/{theme{}/locale (theme folder translate)
- Database Translation:	Database (table core_translate)


### 2. In what way does the developer mode influence how Magento handles translations?

Developer mode doesn’t allow translations not related to a module.

### 3. How many options exist to add a custom translation for any given string?

- Database Translation
- Module Translation
- Theme Translation

### 4. What is the priority of translation options?

- Database Translations
- Theme Translations
- Module Translation

It's worth mentioning that translations are actually loaded in the reverse order. Module translations are loaded first, following by theme and then database translations. But this results in database translations taking precedent.


### 5. How are translation conflicts (when two modules translate the same string) processed by Magento?

Magento stores the translation value in a key => value array. To help resolve conflicts Magento will store a module prefix to the array, if it’s the first translation for a certain key it will also add the translation without the prefix.

    array(
    "AAA" => "BBB",
    "Namespace_Module:AAA" => "BBB"
)

Now if magento finds another module translation with the same key (AAA) it will not update the main key of “AAA” but it will add an additional item to the array with the new prefix, for example:

    array(
    "AAA" => "BBB",
    "Namespace_Module:AAA" => "BBB",
    "Example_Module:AAA" => "CCC"
)

Magento will override the main translation of “AAA” with theme and inline translations. So the preference is based on module load order.

