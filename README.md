This repository is meant to be a collection of known issues in Cheat Engine and
the affected versions so that it's somewhat easy to make something backwards
compatible with at least the last few versions

Obviously bugs are introduced and fixed but there are also new features added,
like a `MainForm` variable being added so you don't have to call `getMainForm()`,
and depending on these can obviously break code. Occasionally something outside
of the CE source code will also cause issues, such as operating system patches

Each issue has it's own file even when many don't necessarily _need_ extra
information eg. `writeSmallInteger` being added in 6.7 since some issues do
need additional information or I simply felt like documenting the source of the
information at the time or have a potential workaround provided.

To avoid having to check all the file names then open a file of additions and
check in there and then a file with modifications and check in there etc.  it's
easier to simply have all issues have their own file with a standard naming
convention so sorting alphabetically does something reasonably sensible and useful

### Naming convention
`<app> [OS_]<version>_<type>_<description>`

## app specification
"app" is short for "applicable to: " in this case, this will almost certainly be `CE`
but if by chance there's something in the tutorial then this could be `TTutX86` or
`GTutX64` or something (DB startd working on a graphical game example after 6.7 to
go with CE hence GTut, not sure when that'll be released since he has mentioned
several other projects as well or if it'll have instructions)

## OS specification
If it's specific to an OS like Mac or Windows then add the OS name before the CE version so that they are together when sorted alphabetically
If it affects all platforms then skip it entirely (`CE <version> ...`)
If you don't know, it's ok to just assume it affects all platforms

## version specification
- prefix file names with version numbers that are affected, eg `CE 6.6`
- For issues that affect multiple concurrent versions use eg CE `6.6-6.7` to indicate 6.5, 6.6, and 6.7
    - For issues that affect all previous versions or have not yet been fixed in a release you can leave off the number but the `-` should still be present to distinguish it from single version issues, eg. `CE -6.7` for anything affecting everything pre CE 6.7 or `CE 6.5-` for something introduced in CE 6.5 and not yet fixed
- For issues that are in multiple versions but are not necessary concurrent, eg. 5.2 and 6.5, 6.6, and 6.7 use a `,` to separate versions though you should still use the `-` for concurrent versions eg. `CE 5.2, 6.5-6.7`
- For issues that affect all versions of CE use `CE ALL`

## type specification
- For bugs use BUG
- For additions to CE eg. the lua function `GetCheatEngineFileVersion` was added in CE 6.7 and thus did not exist prior to that add "ADDITION" after the version
- For changes to existing features, eg. an extra argument being accepted by a function, use "CHANGED"
- For issues not originating with the CE code, such as Intel meltdown/spectre patches breaking DBVM mark it as "EXTERNAL"
- For issues not covered by the previous specification use "OTHER"

Not sure if extended version info, eg. getCheatEngineFileVersion, is necessary... I feel like it's _probably_ not but I'm leaving this note in just in case.
