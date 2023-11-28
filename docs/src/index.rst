TBWrapper
#########

**TBW** is a wrapper to facilitate tensorboard logging. 
Below are some scripts with examples for different data types.

.. note::
   Other data types (e.g., figure, histogram) are available.


SCALAR
======

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs') # path to logging directory
    loss_writer = wrapper('scalar', 'loss')

    for _ in range(10):
        loss_writer(torch.randn(1))

    del wrapper

====


SCALARS
=======

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs')
    loss_writer = wrapper('scalars', 'losses')

    for _ in range(10):
        losses_dict = {'loss_1': torch.randn(1), 
                       'loss_2': torch.randn(1)}
        loss_writer(losses_dict)

    del wrapper

====


IMAGE
=====

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs')
    loss_writer = wrapper('image', 'results')

    for _ in range(10):
        loss_writer(torch.randn((3,128, 128)))

    del wrapper

====


VIDEO
=====

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs')
    loss_writer = wrapper('video', 'results')

    for _ in range(10):
        loss_writer(torch.randn((1, 4, 3,128, 128)), fps=2.0)

    del wrapper

====


TEXT
====

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs')
    text_writer = wrapper('text', 'results')

    for i in range(10):
        loss_writer(f'text string {i}')

    del wrapper

====



EMBEDDING
=========

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs')
    embedding_writer = wrapper('embedding', 'results')
    embedding_writer(torch.randn(10,256), metadata=torch.arange(10))

    del wrapper

====


MULTIPLE WRITERS
================

.. code-block:: python

    import torch
    from tbw import TBWrapper, TBType

    wrapper = TBWrapper('logs') # path to logging directory

    # can directly use enum data types instead
    wrapper(TBType.SCALAR, 'loss')
    wrapper(TBType.IMAGE, 'image')
    wrapper(TBType.VIDEO, 'video')

    for _ in range(10):

        # Find writer objects by tag
        wrapper['loss'](torch.randn(1))
        wrapper['image'](torch.randn(3, 128, 128))

    wrapper['video'](torch.randn(1, 5, 3, 128, 128))

    #optional cleanup
    wrapper['loss'].flush()
    wrapper['image'].flush()
    wrapper['video'].flush()
    del wrapper

====


.. toctree::
   :caption: QUICKSTART
   :glob:
   :hidden:
   :titlesonly:

   installation


.. toctree::
   :caption: API
   :glob:
   :hidden:
   :titlesonly:

   wrapper


.. toctree::
   :caption: Bureau
   :glob:
   :hidden:
   :titlesonly:

   LICENCE


