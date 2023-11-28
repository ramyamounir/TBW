TBWrapper
#########

**TBW** is a wrapper to facilitate tensorboard logging. 
Below are some scripts with examples for different data types.


SCALAR
======

.. code-block:: python

    import torch
    from tbw import TBWrapper

    wrapper = TBWrapper('logs') # path to logging directory
    loss_writer = wrapper('scalar', 'loss')

    for _ in range(10):
        loss_writer(torch.randn(1), flush=True)

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


