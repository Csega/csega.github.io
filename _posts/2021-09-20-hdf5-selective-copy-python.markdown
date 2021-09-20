---
layout: post
title:  "How to copy parts of HDF5 automatically in Python"
date:   2021-09-20 14:22:14 +0200
categories: mypost
---

## Introduction

Hello again, Everyone! Now I had this problem, when I had to copy parts of an HDF5 file. But since the file structure is quite big, I did not want to hardcode all the paths, just discover the structure of the HDF5 and then copy the parts I need using a simple "if" in the code. It wasn't *that* trivial, so I thought I share the snippet, that does exactly this.

## The solution

Actually, I found more than one solution to discover the structure of an HDF5 file, see [this][stackoverflow-hdf5-exploration] link.

What I like the most is this one.

```python
def get_dataset_keys(f):
    keys = []
    f.visit(lambda key : keys.append(key) if isinstance(f[key], h5py.Dataset) else None)
    return keys
```

Simple and elegant, isn't it? :) Now I have all the dataset paths in my HDF5 file, I only need to select the ones I'd like to copy and copy them.

The copy can be a little tricky, so I was looking for some useful snippets again. I found [this][stackoverflow-hdf5-copy] link on Stackoverflow. Using the info here, I compiled the following script.

```python
def copy_hdf5_with_constraints(file_source, file_dest):
    # First getting all the dataset keys.
    keys = get_dataset_keys(file_source)

    fs = h5py.File(file_source, 'r')
    fd = h5py.File(file_dest, 'w')

    for key in keys:
        # Get the name of the parent for the group we want to copy
        print(key)
        if [your_condition_here!]:
            name = key.split("/")[-1]
            group_path = fs[key].parent.name

            # Check that this group exists in the destination file; if it doesn't, create it
            # This will create the parents too, if they don't exist
            group_id = fd.require_group(group_path)
            print(group_path, group_id, name)
            print("-"*50)

            fs.copy(key, group_id, name=name)

    fs.close()
    fd.close()
```

Aaaaaand.... that's it! :)

[stackoverflow-hdf5-exploration]: https://stackoverflow.com/questions/44883175/how-to-list-all-datasets-in-h5py-file
[stackoverflow-hdf5-copy]: https://stackoverflow.com/questions/24510240/how-to-partially-copy-using-python-an-hdf5-file-into-a-new-one-keeping-the-same
