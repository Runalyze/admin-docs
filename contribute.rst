
==========================
Contributing
==========================
Before you do anything else, signup if you haven't and login on GitHub to fork our `GitHub project <https://github.com/Runalyze/Runalyze>`_. Now you can clone your fork locally::

    git clone git@github.com:<your-github-name>/Runalyze.git

This creates a new directory ``runalyze`` with all contents from our repository. Please have a look at our :doc:`Checkout tutorial <checkout>` for further instructions to get that fork running.

Issues
============================
The list of outstanding feature requests and bugs can be found on our on our `GitHub issue tracker <https://github.com/Runalyze/Runalyze/issues>`_. Pick an unassigned issue that you think you can accomplish and add a comment that you are attempting to do it. Feel free to propose issues that are not described!

Setting up topic branches and generating pull requests
======================================================
It's best practice to submit your contribution as pull request on GitHub.
To separate things, please create a "topic branch" for each feature or patch you are working on.
While individual commits allow you control over how small individual changes are made
to the code, branches are a great way to group a set of commits all related to
one feature together, or to isolate different efforts when you might be working
on multiple topics at the same time.

While it takes some experience to get the right feel about how to break up
commits, a topic branch should be limited in scope to a single ``issue`` as
submitted to an issue tracker.

Also since GitHub pegs and syncs a pull request to a specific branch, it is the
**ONLY** way that you can submit more than one fix at a time.  If you submit
a pull from your develop branch, you can't make any more commits to your develop
without those getting added to the pull.

To create a topic branch, its easiest to use the convenient ``-b`` argument to ``git
checkout``::

    git checkout -b patch/for-xyz
    Switched to a new branch 'patch/for-xyz'

You should use a verbose enough name for your branch so it is clear what it is
about.  Now you can commit your changes and regularly merge in the upstream
master as described below.

When you are ready to generate a pull request, either for preliminary review,
or for consideration of merging into the project you must first push your local
topic branch back up to GitHub::

    git push origin patch/for-xyz

Now when you go to your fork on GitHub, you will see this branch listed under
the "Source" tab where it says "Switch Branches".  Go ahead and select your
topic branch from this list, and then click the "Pull request" button.

Here you can add a comment about your branch.  If this in response to
a submitted issue, it is good to put a link to that issue in this initial
comment.  The repo managers will be notified of your pull request and it will
be reviewed (see below for best practices).  Note that you can continue to add
commits to your topic branch (and push them up to GitHub) either if you see
something that needs changing, or in response to a reviewer's comments.  If
a reviewer asks for changes, you do not need to close the pull and reissue it
after making changes. Just make the changes locally, push them to GitHub, then
add a comment to the discussion section of the pull request.

Pull upstream changes into your fork regularly
==================================================

It is critical that you pull upstream changes from master into your fork on a regular basis. Nothing is worse than putting in a days of hard work into a pull request only to have it rejected because it has diverged too far from develop. 

To pull in upstream changes::

    git remote add upstream https://github.com/Runalyze/Runalyze.git
    git fetch upstream master

Check the log to be sure that you actually want the changes, before merging::

    git log upstream/master

Then merge the changes that you fetched::

    git merge upstream/master

For more info, see http://help.github.com/fork-a-repo/

How to get your pull request accepted
=====================================

We want your submission. But we also want to provide a stable experience for our users and the community. Follow these rules and you should succeed without a problem!

Run the tests!
--------------
Before you submit a pull request, please run all unit tests via::

    ./vendor/bin/phpunit -c tests/config.xml

Travis CI will run these tests as well but it's bad practice to wait for these results as you can run all tests locally.
You may need to create (or update) a test database if you haven't done so::

    mysql -uroot -e 'SET @@global.sql_mode = TRADITIONAL; CREATE DATABASE runalyze_test; CREATE DATABASE runalyze_unittest;'
    mysql runalyze_unittest < inc/install/structure.sql

If you add code you need to add tests!
--------------------------------------------
Please add test cases if you have added new classes or methods. Code without tests is undependable.

Also, keep your tests as simple as possible. Complex tests end up requiring their own tests. We would rather see duplicated assertions across test methods then cunning utility methods that magically determine which assertions are needed at a particular stage. Remember: `Explicit is better than implicit`.

Follow our coding guidelines
---------------------------------------
Your code should follow `PSR-1 <http://www.php-fig.org/psr/psr-1/>`_ and `PSR-2 <http://www.php-fig.org/psr/psr-2/>`_.
In addition, please follow some general guidelines for clean code. This includes for example:

* **loose coupling**: different classes should know as less as possible about each other
* **high cohesion**: methods and properties of a single class should belong to each other
* **single responsibility**: a class should have one and only one reason to charge (the same applies for methods)
* **small classes**: there must be a really good reason if a class exceeds 200 lines
* **short methods**: there must be a really good reason if a method exceeds 20 lines
* **descriptive names**: variable and method names should be descriptive, there is no need to use funky abbreviations

