# Next.js Issue Repository

This repository reproduces reload infinitely.

My understandings are here:

+ next.js creates compiled javascript `index.js` object if user accesses. 
+ on-demand-entry-handler.js removes inactive pages on every 60 secs.
+ if user access pages e.g. "/", "/about", on-demand-entry-handler saves the path. and preserve the filepath.
+ however, **trailing slash module** removes slash, if slash is removed, lastAccessPage is changed. like `"/"` => `""`.
+ user current page is not identified to "lastAccessPage".
+ on-demand-entry-handler disposes compiled javascript `index.js`.
+ `amp-dev.js` reloads current page because current page is changed.
+ next.js re-creates the compiled javascript `index.js`.


