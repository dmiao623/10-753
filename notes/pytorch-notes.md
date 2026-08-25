### Data Processing

Pytorch has two primitives for loading data: `torch.utils.data.DataLoader` and `torch.utils.data.Dataset`. `Dataset` stores samples and `DataLoader` wraps it in an iterable.

Specifically, `DataLoader` accepts a `dataset` argument that can be a map-style dataset or an iterable dataset.
- Map-style datasets are used when retrievals are cheap. They implement the `__getitem__` and `__len__` functions. The `__getimes__` method can be overridden as well for speedup batched sample loading.
- Iterable datasets are subclasses of `IterableDataset` that implement `__iter__` and returns a stream of data.

For map-style datasets, the `shuffle`, `sampler`, `batch_sampler`, `batch_size`, `drop_last`, and `collate_fn` arguments control the sampling process.
- The `batch_size` and `drop_last` argument allow the user to construct a `batch_sampler` from a given `sampler` object.
- The `collate_fn` argument is used to collate lists of samples into a batch, e.g. by stacking into a tensor along the first dimension.

The `num_workers` arguments allows parallelization across threads.