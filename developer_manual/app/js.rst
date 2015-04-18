==========
JavaScript
==========

.. sectionauthor:: Bernhard Posselt <dev@bernhard-posselt.com>

The JavaScript files reside in the **js/** folder and should be included in the template:

.. code-block:: php

  <?php
  // add one file
  script('myapp', 'script');  // adds js/script.js

  // add multiple files in the same app
  script('myapp', array('script', 'navigation'));  //  adds js/script.js js/navigation.js

  // add vendor files (also allows the array syntax)
  vendor_script('myapp', 'script');  //  adds vendor/script.js

The recommended JavaScript framework to use is `AngularJS <https://angularjs.org/#>`_. A nice tutorial screencast collection can be found on `Egghead.io <https://egghead.io/technologies/angularjs>`_

Sending the CSRF token
======================
If any other JavaScript request library than jQuery is being used, the requests need to send the CSRF token as an HTTP header named **requesttoken**. The token is available in the global variable **oc_requesttoken**.

For AngularJS the following lines would need to be added:

.. code-block:: js

    var app = angular.module('MyApp', []).config(['$httpProvider', function($httpProvider) {
        $httpProvider.defaults.headers.common.requesttoken = oc_requesttoken;
    }]);


Generating URLs
===============
To send requests to ownCloud the base URL where ownCloud is currently running is needed. To get the base URL use:

.. code-block:: js

    var baseUrl = OC.generateUrl('');

Full URLs can be genrated by using:

.. code-block:: js

    var authorUrl = OC.generateUrl('/apps/myapp/authors/1');
