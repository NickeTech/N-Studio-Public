# ❓ How can I localize/translate N-Studio?

_First thing, check if the translation isn't already done! Or up to date._ 

### 📃 Requirements

1. A **text editor** or maybe **Visual Studio**.
2. The `Strings.en.xaml` file, that contains all the translatable text.
3. The language code (`LCID`) of your translation, something like `pt-BR` or `en`. It can be specific to a region or generic to an entire language branch.

_A generic translation acts as a fallback resource if a specific translation bound to the region of your environment is not present._

en <- es <- es_AR

For example: 
1) If the word "OK" is the same in Spanish and in Argentinian Spanish, you don't need to have the text in both because it's already available in the base English file.
2) If "Aceptar" is the same in Spanish and Argentinian Spanish, you only need the text in the base Spanish file.

### 📡 Acquiring the translatable texts

1. Head over to the Localization folder in this repository.
2. Download/copy any of the **xaml** files. (I recommend to download the [English](https://raw.githubusercontent.com/NickeTech/N-Studio-Public/master/Localizations/Strings.en.xaml) version or the [Brazilian Portuguese](https://raw.githubusercontent.com/NickeTech/N-Studio-Public/master/Localizations/Strings.pt.xaml) because they are always updated)
3. When saving the text, please use the UTF-8 encoding.

### ✏ Translating

_It looks easy, but there's a lot to translate._

Each `<s:String...` tag represents a translatable string, you just need to translate the content of that tag:

`<s:String x:Key="S.Imperative.Accept">Accept</s:String>`

English to Brazilian Portuguese.

`<s:String x:Key="S.Imperative.Accept">Aceitar</s:String>`

_To represent a new line, you can use `&#10;` and to represent a carriage return + new line, use `&#13;` `&#10;`_

`<s:String x:Key="S.Example">First line&#10;Second line</s:String>`

### 💾 File naming

Simple, name like (replace with your LCID): 

**Strings.**pt-BR**.xaml**

## 🧪 Testing

You can test your translations by using the importer.

Go to **Settings** > **Application** > Select `Custom` and a popup will appear, then import your custom `xaml` file selecting your target language. 

_There's a fallback mechanism, if one text entry is not found within the active localization, it will search inside the fallback one or the English variant._

_Also, there's a problem with this feature, special characters such as **CarriageReturn/NewLine**: (&amp;#10; &amp;#13;) may not appear correctly, but they will after I release your translation with the app._

## 📩 After it's done

* You can send the `xaml` file as attachment to [nicke@outlook.com.br](malito:nicke@outlook.com.br). Don't forget to provide your name or nickname.
* Or make a pull request (PR) using Git:
    1. [Create a fork](https://help.github.com/articles/fork-a-repo/) of this repository.
    2. Add your new or updated translation to the forked project (you can visit your forked project web page and simply upload the file to the folder Localizations).
    3. [Create a pull request with your changes.](https://help.github.com/articles/creating-a-pull-request/)
