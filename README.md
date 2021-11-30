# Typescript Snippets

<!--
Add a banner image and badges
 -->

If you look closely, you'll notice that most of your favorite NPM packages aren't written in Javascript. They're written in a fancy, new language, called "Typescript" - and for a good reason. Typescript helps you discover everything your favorite NPM packages have to offer: all of their functions, classes and interfaces. But Typescript has a steep learning curve, and your first Typescript file is the hardest to write. These snippets make it easier.

- **Stub Typescript classes with the `typescript-class` snippet**

  ![typescript-class snippet](.readme/clip-typescript-class.gif)

  Write `typescript-class` in any `.ts` file, and select the 'Typescript Class' snippet from VScode's intellisense menu. VScode will stub out an empty class, with tab stops for all of the fields that you need to fill out to customize your class.

- **Stub [TSdoc](https://tsdoc.org) sections with the `class`, `method`, and `const` snippets**

  ![TSdoc class section](.readme/clip-tsdoc-section-class.gif)

  Write `class` in any `.ts` file and select the `TSdoc Class` snippet from VSCode's intellisense menu. VScode will stub out a TSdoc block with tab stops for all of the fields you need to customize to document your class.

- **Add TSdoc tags to TSdoc sections with the `decorator`, `deprecated`, `defaultValue`, `example`, `param`, `privateRemarks`, `remarks`, `returns`, `see`, `throws`, `typeParam` and `mod` snippets**

  ![TSdoc modifiers snippet.](.readme/clip-tsdoc-tag-modifiers.gif)

  Write `decorator`, `deprecated`, `defaultValue`, `example`, `param`, `privateRemarks`, `remarks`, `returns`, `see`, `throws` or `typeParam` in any TSdoc block, and vscode will add the corresponding [tag](https://tsdoc.org/pages/spec/tag_kinds/) to the block, along with tab stops for the tag's fields.

<!-- list any codebases, websites, apps, platforms or other products that use your code -->

<!-- link to your reader to your repository's bug page, and let them know if you're open to contributions -->

## Usage:

The best way to take advantage of Typescript is to organize your code into classes. But classes are intricate: they have static methods, private variables, private methods, instance methods, accessors and constructors. If you're new to Typescript development, it can be hard to remember these pieces when you're staring at a blank document. Lucky for you, the `typescript class` clip keeps track of these pieces for you. Use it to to stub out a Typescript class. Once you do, you can focus on what your class does, rather than how it's formatted.
![typescript-class clip](.readme/clip-typescript-class.gif)

Once you write your typescript code, you probably want to share it with someone else. But, before you do that, you should document what it does, and why you wrote it, with TSdoc.

Typescript's first-class support for classes, interfaces, and type declarations makes it easy for programmers to independently write pieces of code that fit together. However, typescript doesn't share the **context** behind the code. The context includes:

1. Why the code was written in the first place.
2. Who the code helps, and what it helps them do.
3. How the code can be used.
4. How the code shouldn't be used.

TSdoc is _the_ standard way to add context to your code. It splits your documentation into **sections**, each of which corresponds to a single function, variable, class or method. It further splits each section into **tags**. Each tag describes a different aspect of the section. Together, they give other developers a comprehensive understanding of the code you wrote. As an added bonus, TSdoc also formats your documentation into a website or markdown file, with [Typedoc](https://typedoc.org).

### Use TSdoc Sections

To use TSdoc, you need to write your documentation inside multi-line comments:

- TSdoc ONLY pays attention to multi-line comments: i.e.:

  ```typescript
  /**
   * comment
   */
  ```

- TSdoc completely ignores single-line comments: i.e.:

  ```typescript
  // comment
  ```

  ```typescript
  /* comment */
  ```

If you don't like manually typing out multi-line comments. No problem, just use the `/doc` clip I've provided.

<!-- show gif of doc snippet -->

TSdoc lumps everything within a multiline comment into a single section:

```typescript
/**
 * This is a section
 */

/**
 * This is another section
 */
```

To split your documentation into sections, all you need to do is make a multiline comment for each section.

But where do you put each section? TSdoc expects you to put each section directly before the piece of code it describes:

```typescript
/**
 * This section describes `const CoffeeBeans`
 */
const CoffeeBeans = 'French Roast';

/**
 * This section describes `function grindCoffeeBeans(...)`
 */
function grindCoffeeBeans(beans: string): string {
  //...
}

/**
 * This section describes `class CoffeeBeanGrinder{ ... }`
 */
class CoffeeBeanGrinder {
  //...

  /**
   * This section describes `public grind(beans:string):string
   */
  public grind(beans: string): string {
    //...
  }
}
```

Every TSdoc section contains a summary, a set of blocks and a list of modifiers:

```typescript
/**
 * <Summary>
 *
 * <Block>
 *
 * <Block>
 *
 * <Block>
 *
 * <Modifier>
 */
```

The summary should contain up to three sentences that explains what the corresponding code does. E.g.:

```typescript
/**
 * GrindCoffeeBeans turns whole beans into powder. It can accept any kind of coffee beans, and can be adjusted to grind powder at varying levels of coarseness.
 *
 * <Block>
 *
 * <Block>
 *
 * <Block>
 *
 * <Modifier>
 */
```

Each block contains a single tag, followed by supporting documentation. You can even format this documentation with [markdown](https://github.com/microsoft/tsdoc/issues/12) and [code fences](https://github.com/microsoft/tsdoc/issues/20) if you want.

```typescript
/**
 * grindCoffeeBeans turns whole beans into powder. It can accept any kind of coffee beans, and can be adjusted to grind powder at varying levels of coarseness.
 *
 * @param beans - the coffee beans you want to grind
 *
 * @returns coffee powder
 *
 * @remarks
 * grindCoffeeBeans actually makes use of the static method {@link CoffeeBeanGrinder.grind} under the hood.
 *
 * <Modifier>
 */
```

The list of modifiers contains tags separated by spaces, none of which are followed by text. E.g.:

```typescript
/**
 * grindCoffeeBeans turns whole beans into powder. It can accept any kind of coffee beans, and can be adjusted to grind powder at varying levels of coarseness.
 *
 * @param beans - the coffee beans you want to grind
 *
 * @returns coffee powder
 *
 * @remarks
 * grindCoffeeBeans actually makes use of the static method {@link CoffeeBeanGrinder.grind} under the hood.
 *
 * @alpha @experimental
 */
```

If all of this is a lot to remember, don't worry, I've made a few clips that make it a LOT easier:

#### Use the `class` clip to document a class. It expands to:

![TSdoc class clip](.readme/clip-tsdoc-section-class.gif)

````typescript
/**
 * What is the class's single responsibility?
 *
 * @remarks
 * When should you use the class? What performance benefits or other magical powers does it confer upon you?
 * When shouldn't you use the class?
 * What states does this class furnish?
 * What behaviors does this class furnish?
 * Can you inject dependencies into this class?
 * Are there any situations where it makes sense to extend this class, rather than inject dependencies into it?
 * How does the code in this class work?
 *
 * @example
 * ```typescript
 *	// example of how to use this class here
 * ```
 *
 * @alpha @beta @eventProperty @experimental @internal @override @packageDocumentation @public @readonly @sealed @virtual
 */
````

#### Use the `method` clip to document a method or function. It expands to:

![](.readme/clip-tsdoc-section-method.gif)

```typescript
/**
 * What does this method or function do?
 *
 * @param name - description
 *
 * @returnstype and meaning of return value
 *
 * @alpha @beta @eventProperty @experimental @internal @override @packageDocumentation @public @readonly @sealed @virtual
 */
```

#### Use the `const` clip to document a variable. It expands to:

![](.readme/clip-tsdoc-section-variable.gif)

```typescript
/**
 * Summary
 *
 * Block Tags
 *
 * @alpha @beta @eventProperty @experimental @internal @override @packageDocumentation @public @readonly @sealed @virtual
 */
```

### Use TSdoc tags:

Remember how I mentioned that every TSdoc section has a summary, blocks, and a list of modifiers? Some tags describe blocks, and others describe modifiers. But that's not all - you can actually tags _within_ blocks. Here are all of the following [tags](https://tsdoc.org/mobile_nav) you can use, grouped by what they describe:

#### Tags that describe blocks:

| Tag                                                             | Trigger                                                                                                  | What it does:                                                                                                                                                        |
| :-------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [@decorator](https://tsdoc.org/pages/tags/decorator/)           | `decorator`<br/><img src=".readme/clip-tsdoc-tag-decorator.gif" alt="trigger decorator"/>                | Quotes an [ES6 decorator](https://www.typescriptlang.org/docs/handbook/decorators.html) expression.                                                                  |
| [@deprecated](https://tsdoc.org/pages/tags/deprecated/)         | `deprecated`<br/><img src=".readme/clip-tsdoc-tag-deprecated.gif" alt="trigger deprecated"/>             | Deprecates the code it documents, and recommends an up-to-date alternative.                                                                                          |
| [@defaultValue](https://tsdoc.org/pages/tags/defaultvalue/)     | `defaultValue`<br/><img src=".readme/clip-tsdoc-tag-defaultvalue.gif" alt="trigger defaultValue"/>       | Lists value that a property of a class or interface will have if it isn't set.                                                                                       |
| [@example](https://tsdoc.org/pages/tags/example/)               | `example`<br/><img src=".readme/clip-tsdoc-tag-example.gif" alt="trigger example"/>                      | Demonstrates how to use the code it documents.                                                                                                                       |
| [@param](https://tsdoc.org/pages/tags/param/)                   | `param`<br/><img src=".readme/clip-tsdoc-tag-param.gif" alt="trigger param"/>                            | Describes an argument of a method or function.                                                                                                                       |
| [@privateRemarks](https://tsdoc.org/pages/tags/privateremarks/) | `privateRemarks`<br/><img src=".readme/clip-tsdoc-tag-privateremarks.gif" alt="trigger privateRemarks"/> | Contains documentation that should be omitted from any auto-generated documentation site.                                                                            |
| [@remarks](https://tsdoc.org/pages/tags/remarks/)               | `remarks`<br/><img src=".readme/clip-tsdoc-tag-remarks.gif" alt="trigger remarks"/>                      | Contains an explanation of the implementation details, reasoning, or any other long-form contextual information about the code it documents.                         |
| [@returns](https://tsdoc.org/pages/tags/returns/)               | `returns`<br/><img src=".readme/clip-tsdoc-tag-returns.gif" alt="trigger returns"/>                      | Describes what returns from a method or function.                                                                                                                    |
| [@see](https://tsdoc.org/pages/tags/see/)                       | `see`<br/><img src=".readme/clip-tsdoc-tag-see.gif" alt="trigger see"/>                                  | Lists links to other sections of the documentation or websites.                                                                                                      |
| [@throws](https://tsdoc.org/pages/tags/throws/)                 | `throws`<br/><img src=".readme/clip-tsdoc-tag-throws.gif" alt="trigger throws"/>                         | Lists any errors that a method or function throws.                                                                                                                   |
| [@typeParam](https://tsdoc.org/pages/tags/typeparam/)           | `typeParam`<br/><img src=".readme/clip-tsdoc-tag-typeparam.gif" alt="trigger typeParam"/>                | Describes the types you can insert into the type argument of a [generic](https://www.typescriptlang.org/docs/handbook/2/generics.html) function, interface or class. |

#### Tags that describe phrases within blocks (also known as inline tags):

| Tag                                                     | Trigger                                                                                      | What it does:                                                                                  |
| :------------------------------------------------------ | :------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------- |
| [@inheritDoc](https://tsdoc.org/pages/tags/inheritdoc/) | `inheritDoc`<br/><img src=".readme/clip-tsdoc-tag-inheritdoc.gif" alt="trigger inheritDoc"/> | Copies the `@remarks` `@params` `@typeParam` from another section into the current section.    |
| [@label](https://tsdoc.org/pages/tags/label/)           | `label`<br/><img src=".readme/clip-tsdoc-tag-label.gif" alt="trigger label"/>                | Adds an arbitrary label to the block that contains it, so that the block can be referenced it. |
| [@link](https://tsdoc.org/pages/tags/link/)             | `link`<br/><img src=".readme/clip-tsdoc-tag-link.gif" alt="trigger link"/>                   | Links to another section, or a website.                                                        |

#### Tags that describe modifiers

Note that the `@mod` clip expands to: `@alpha @beta @eventProperty @experimental @internal @override @packageDocumentation @public @readonly @sealed @virtual`. This includes all of the available modifier clips, each of which occupies its own tab stop. This makes it east to choose the ones you want. Keep in mind that you **must** place these modifiers on the [LAST](https://tsdoc.org/pages/spec/tag_kinds/) line of the TSdoc comment.

<table>
<thead>
<tr>
<th align="left">Tag</th>
<th align="left">Trigger</th>
<th align="left">What it does:</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/alpha/">@alpha</a></td>
<td align="left" rowspan="11" valign="top"><code>mod</code><br/><img src=".readme/clip-tsdoc-tag-modifiers.gif" alt="mod trigger"/></td>
<td align="left">Marks code as an 'alpha' release.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/beta/">@beta</a></td>
<td align="left">Marks code as a 'beta' release.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/eventproperty/">@eventProperty</a></td>
<td align="left">Indicates that a method returns a <a href="https://developer.mozilla.org/en-US/docs/Web/API/Event">Browser Event</a> or <a href="https://nodejs.org/api/events.html">Node Event</a>.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/experimental/">@experimental</a></td>
<td align="left">Marks code as 'experimental' release.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/internal/">@internal</a></td>
<td align="left">Excludes code from a public API.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/override/">@override</a></td>
<td align="left">Marks a class as overriding the class from which it inherits.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/packagedocumentation/">@packageDocumentation</a></td>
<td align="left">Indicates that a section describes an entire package - not just the code it immediately precedes. <strong>This should only ever be used in the package's entry <code>.d.ts file.</code></strong></td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/public/">@public</a></td>
<td align="left">Marks code as a stable, 'public' release. This code shouldn't change.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/readonly/">@readonly</a></td>
<td align="left">Marks a variable or property as being read-only.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/sealed/">@sealed</a></td>
<td align="left">Indicates that a class should never be extended.</td>
</tr>
<tr>
<td align="left"><a href="https://tsdoc.org/pages/tags/virtual/">@virtual</a></td>
<td align="left">Indicates that a class can not only be extended, but can also be overridden without consequence.</td>
</tr>
</tbody>
</table>

When you use any of the above clips within a TSdoc section, it will automatically add in the tag name, and a placeholder for any additional text that follows the tag.

### How Typescript Snippets works:

This extension [contributes the `snippets/snippets.code-snippets` file to VScode.](https://code.visualstudio.com/api/language-extensions/snippet-guide) When you install this extension in VScode, it grabs the snippets in this file, and offers them as intellisense suggestions when you

## Roadmap:

See [`CHANGELOG.md`](https://github.com/incremental-design/app-stencils/blob/ajay-dev/libs/snippets/vscode/typescript-snippets-for-vscode/typescript-snippets/CHANGELOG.md)

## Contribute to Project Name:

To contribute to this project, you need to set up the `app-stencils` monorepo, as follows:

### Setup:

The code for this extension lives in the [incremental.design/app-stencils](https://github.com/incremental-design/app-stencils) monorepo. To contribute to this extension's code, you need to set up this monorepo. See [`CONTRIBUTE.md`](https://github.com/incremental-design/app-stencils/blob/ajay-dev/CONTRIBUTE.md) to learn how.

#### Repository Structure:

| File or Folder                  | What does it do?                                                                                               | When should you modify it?                                                                 |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------- |
| .readme/                        | Contains all of the images used in this README. Note that everything in this folder is versioned with Git LFS. | Whenever you need to add or change the images used in this README.                         |
| snippets/snippets.code-snippets | Contains all of the [snippets](#snippets) that this extension provides.                                        | Whenever you need to change any of the [snippets](#snippets) that this extension provides. |
| .vscodeignore                   | Lists the files that will not be included in this extension when its' published.                               | Never.                                                                                     |
| CHANGELOG.md                    | Lists the changes that each version introduces.                                                                | Whenever you increment this package's version in [`package.json`](./package.json)          |
| package.json                    | Describes the contents, scripts, and configuration details of this extension.                                  | Whenever you need to release a new version of this package.                                |
| README.md                       | This file.                                                                                                     | Whenever you add or change a snippet in this extension.                                    |

### Develop:

See [Visual Studio Code ➝ Create your own snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_create-your-own-snippets)

### Test:

1. Open the `libs/snippets/vscode/typescript-snippets-for-vscode` folder in the current VScode window.

   ![Open the extension folder in the current window.](.readme/test-extension-1.gif)

2. Hit [`F5`]() to load the snippets in a new VScode window.

   ![Load snippets in a new VScode window.](.readme/test-extension-2.gif)

3. Create a new Typescript file, or open an existing one.

   ![Create a new file and set syntax to Typescript.](.readme/test-extension-3.gif)

4. Test the snippets you just made.

   ![Test the `typescript-class` snippet.](.readme/test-extension-4.gif)

5. Whenever you save changes to the snippets, hit the 'reload' button in the debugger tray to send the changes to the VScode window.

   ![Press the reload button.](.readme/test-extension-5.gif)

<!--
  to publish:

  go to https://dev.azure.com/<publisher-name>/_usersSettings/tokens where <publisher-name> is the user account under which this extension is published

  get a personal access token (see: https://code.visualstudio.com/api/working-with-extensions/publishing-extension#get-a-personal-access-token )

  then `vsce login <publisher-name>` and supply the personal access token you just got.

  then increment the version number in `package.json`, add an entry for that vesion number ot `CHANGELOG.md` and finally `yarn publish-extension`.
 -->
