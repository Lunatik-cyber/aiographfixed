aiographfixed
===========

|shield-pypi| |shield-pypi-status| |shield-travis| |shield-codecov| |shield-license|

**aiographfixed** - asynchronous Python Telegra.ph API wrapper, that fix aiograph

Annotations
-----------
The Telegraph class (``aiographfixed.Telegraph``) encapsulates all API calls in a single class.
It provides functions such as create_page, get_views and other's methods described at `Telegra.ph/api <http://telegra.ph/api>`_ page

All data types  stored In the package ``aiographfixed.types``.

All methods are named following the `PEP-8 <https://www.python.org/dev/peps/pep-0008/>`_ instructions
for example ``create_account`` for ``createAccount`` method and etc.
All API methods are awaitable and can be called only inside Event-loop.

Also if you want to upload the file to Telegra.ph service use ``upload`` method
from the instance of Telegraph class.

By the end of all actions you will need to close HTTP connections by calling the `close()` method (is awaitable).


Installation
------------

Using PIP
~~~~~~~~~
.. code-block:: bash

    $ pip install -U aiographfixed

From sources
~~~~~~~~~~~~
.. code-block:: bash

    $ git clone https://github.com/Lunatik-cyber/aiographfixed.git
    $ cd aiographfixed
    $ python setup.py install


Usage examples
--------------

.. code-block:: python3

   import asyncio

   from aiographfixed import Telegraph

   loop = asyncio.get_event_loop()
   telegraph = Telegraph()


   async def main():
       await telegraph.create_account('aiograph-demo')
       page = await telegraph.create_page(title='Demo', content='<p><strong>Hello, world!</strong></p>', public=True)
       print('Created page:', page.url)


   if __name__ == '__main__':
       try:
           loop.run_until_complete(main())
       except (KeyboardInterrupt, SystemExit):
           pass
       finally:
           loop.run_until_complete(telegraph.close())  # Close the aiohttp.ClientSession


Links
-----

- News: `@aiogram_live <https://t.me/aiogram_live>`_
- Community: `@aiogram <https://t.me/aiogram>`_
- Russian community: `@aiogram_ru <https://t.me/aiogram_ru>`_
- Pip: `aiographfixed <https://pypi.org/project/aiographfixed>`_
- Source: `Github repo <https://github.com/Lunatik-cyber/aiographfixed>`_
- Issues/Bug tracker: `Github issues tracker <https://github.com/Lunatik-cyber/aiographfixed/issues>`_

.. |shield-pypi| image:: https://img.shields.io/pypi/v/aiograph.svg?style=flat-square
   :target: https://pypi.org/project/aiographfixed/
   :alt: PyPI

.. |shield-pypi-status| image:: https://img.shields.io/pypi/status/aiograph.svg?style=flat-square
   :target: https://pypi.org/project/aiographfixed/
   :alt: PyPi status

.. |shield-travis| image:: https://img.shields.io/travis/aiogram/aiograph.svg?branch=master&style=flat-square
   :target: https://travis-ci.org/aiogram/aiographfixed
   :alt: Travis-CI

.. |shield-codecov| image:: https://img.shields.io/codecov/c/github/aiogram/aiograph.svg?style=flat-square
   :target: https://codecov.io/gh/aiogram/aiographfixed
   :alt: Codecov

.. |shield-license| image:: https://img.shields.io/pypi/l/aiogram.svg?style=flat-square
   :target: https://opensource.org/licenses/MIT
   :alt: MIT License
