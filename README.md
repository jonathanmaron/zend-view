# zend-view

[![Build Status](https://secure.travis-ci.org/zendframework/zend-view.svg?branch=master)](https://secure.travis-ci.org/zendframework/zend-view)
[![Coverage Status](https://coveralls.io/repos/zendframework/zend-view/badge.svg?branch=master)](https://coveralls.io/r/zendframework/zend-view?branch=master)

zend-view provides the “View” layer of the Zend Framework MVC system. It is a
multi-tiered system allowing a variety of mechanisms for extension,
substitution, and more.

- File issues at https://github.com/zendframework/zend-view/issues
- Documentation is at https://zendframework.github.io/zend-view/

## Forked

On June 30, 2019, Zend\View was forked.

To vastly improve performance in a very large Navigation tree, the "accept()" call now always returns "true" (li 315):

    public function accept(AbstractPage $page, $recursive = true)

    vendor/zendframework/zend-view/src/Helper/Navigation/AbstractHelper.php

This reduced the lookup time in the Navigation tree from:

    0.51467514038086 s, 3.1678 s
    
to:

    0.049877882003784 s, 0.5161 s

The first number is the time to for one call to the Navigation tree, the second the page execution time (page contained several calls to Navigation).

This only works, since we are not using the Visible flag nor the ACL functionality.
