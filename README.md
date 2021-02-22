# aiida-repository (test)

**NOTE! THIS WAS JUST A FIRST PROOF OF CONCEPT OF THE AIIDA FILE REPOSITORY.**
**This was the reimplemented in AiiDA (using similar concepts) and will appear in AiiDA 2.0.**

**This repo is now archived (it is here just for historical reasons). Refer to the AiiDA implementation instead.**

A simple mock-up of a possible new implementation of the AiiDA repository,
leveraging the disk-objectstore package.

NOTE: you need to install first the [disk-objectstore](https://github.com/giovannipizzi/disk-objectstore) package.
This is not yet on pip, so you need to get it with `git` and pip install it
in editable mode.

## Goal
This is not meant to be a final implementation, but just a simple mock-up
implementation to test the interface, and the performance.

In particular, the most useful code is the `example_repository.py` file,
that can be run to try to export an existing AiiDA "legacy" repository (AiiDA v1.1 and earlier) into a new format using the disk-objectstore.

In order to run it, you can create a bash file with the following content:
```bash
#!/bin/bash
./example_repository.py -U "DB_USERNAME" -D test_repo -P "YOURPWD" -c -r ~/.aiida/repositories/aiidadb/repository/ -C "$@"
```

Replace `DB_USERNAME` and `YOURPWD` with the user name and password of a user that can connect to PostgreSQL.
`test_repo` can be changed to the name of a different database.

**VERY IMPORTANT NOTE!** You need to create `test_repo` first. But, **most importantly**,
note that this needs to be a test database, as this will be DROPPED by the tests inside
`example_repository.py`.
