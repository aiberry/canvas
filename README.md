### Spend time

Main part: about 30 working hours

# Additional tasks

5. Spend time - about an hour. Eslint were installed with Vue app creating

Lint:
Here was one eslint error in components/Table.vue. Function fillHeaderColors takes additional unneccery arguments. So adding comment "
// eslint-disable-next-line @typescript-eslint/no-unused-vars" before function solved the problem

Stylelint:

Added .stylelingignore to ignore .ico, .png, .tsconfig, package.json files. In json files were one error in each, that seemed like bug

Added comment in components/Table.vue: /_ stylelint-disable selector-no-qualifying-type _/. If to set class selector, it ruins because of classnames are changed to special values

### Bugs/Problems

As vue CLI works with Webpack there is no need of explicit adding of it.

To see Webpack configuration run "yarn inspect"

Known issue:

In components/CanvasField.vue preset three errors, which dont affect code execution.

1. and 2) Property 'getContext' does not exist on type 'Vue | Element | Vue[] | Element[]'.
   Property 'getContext' does not exist on type 'Vue'.

2. Cannot find name 'Buffer'. Do you need to install type definitions for node? Try `npm i @types/node` and then add `node` to the types field in your tsconfig.

Possibliy they related with Typescript. Probably, they might be fixed with editing tsconfig. Time to research about hour.
