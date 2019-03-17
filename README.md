Install
-------
Requirements:

* [Tensorpack][]: clone and `pip install -e .`
* [LMDB][]: `pip install lmdb`
* [OpenCV][]: `pip install opencv-python`
* [Protobuf][]: `conda install protobuf`
* [python-prctl][]: clone, `sudo apt-get install build-essential libcap-dev` and `python setup.py build`

[tensorpack]: https://github.com/ppwwyyxx/tensorpack
[lmdb]: https://lmdb.readthedocs.io/en/release/
[tqdm]: https://pypi.python.org/pypi/tqdm
[opencv]: https://pypi.python.org/pypi/opencv-python
[Protobuf]: https://github.com/google/protobuf

`Tensorpack` version > 0.9 is currently NOT supported.
Note thatome prebuilt opencv is much slower than others. Remember to check with [this script](https://github.com/tensorpack/benchmarks/blob/master/ImageNet/benchmark-opencv-resize.py) and make sure it prints < 1s.

### Preprocessing

To start, set the environment variable `IMAGENET` to the ILSVRC2012 
dataset. `TENSORPACK_DATASET` should also be set (for tensorpack).

```script
export IMAGENET='/mnt/work/data/raw-data/'
python preprocess_sequential.py
```

### Usage

```
train_loader = LMDBLoader('train', batch_size=args.batch_size, num_workers=32, shuffle=True, cuda=True)
valid_loader = LMDBLoader('val', batch_size=args.batch_size, num_workers=32, shuffle=False, cuda=True) 

```
## TODO 
- [ ] Image Normalization
- [ ] Support HDF5 format
- [ ] Tensorpack version > 0.9

### Disclaimer

Code mainly from [sequential-imagenet-dataloader](https://github.com/BayesWatch/sequential-imagenet-dataloader), and [Tensorpack](https://github.com/tensorpack/tensorpack) examples.

### Reference

[Data loader takes a lot of time for every nth iteration](https://discuss.pytorch.org/t/data-loader-takes-a-lot-of-time-for-every-nth-iteration/10831)
[First batch of Imagenet training is slow with sequential loading](https://discuss.pytorch.org/t/first-batch-of-imagenet-training-is-slow-with-sequential-loading/11464)
[How to prefetch data when processing with GPU?](https://discuss.pytorch.org/t/how-to-prefetch-data-when-processing-with-gpu/548)
[How to speed up the data loader](https://discuss.pytorch.org/t/how-to-speed-up-the-data-loader/13740)
[Fast data loader for Imagenet](https://discuss.pytorch.org/t/fast-data-loader-for-imagenet/988/14)

