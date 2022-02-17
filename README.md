# pl-lt-rules
Rules for writing academic papers and checking them using [LTex language server](https://github.com/valentjn/ltex-ls) and [LanguageTool](https://github.com/languagetool-org/languagetool) 

This is an incomplete, highly opinionated list of rules I use in LanguageTool for checking my papers. Feel free to use it, modify it, etc.
The rules are geared towards programming-language papers.

Many of the rules are taken from [this guide](https://capra.cs.cornell.edu/styleguide/#runtime)

Pull requests and bug reports are always welcome!

## Using

1. Run LanguageTool as a server, following [this guide](https://dev.languagetool.org/http-server.html). This lets you modify your grammar rules.

2. Add the rules to your grammar. Add a line that looks something like this under `<!DOCTYPE rules [` in LanguageTool's `grammar.xml`:

    ```xml
        <!ENTITY UserRules SYSTEM "file:///path/to/your/rules">
    ```

    Then in some enabled rule-set, add `&UserRules;`. For example, I have:
    
    ```xml
    <rules lang="en-GB" xsi:noNamespaceSchemaLocation="../../../../../../../../../../languagetool-core/src/main/resources/org/languagetool/rules/rules.xsd"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <category id="SEMANTICS" name="Semantics" type="inconsistency">

    <!-- English rule, 2022-02-01 -->
            &UserRules;

    ```

    The full guide is [here](https://dev.languagetool.org/tips-and-tricks)

4. Restart the LanguageTool server each time you change the rules.

## Guides/toops for making rules:

* [LanguageTool Rule Creator](https://community.languagetool.org/ruleEditor2/)
* [LanguageTool rules overview](https://dev.languagetool.org/development-overview)
* [Chunking in LanguageTool](https://dev.languagetool.org/using-chunks)
