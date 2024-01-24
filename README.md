# Microstart
[![License](https://poser.pugx.org/t3brightside/microstart/license)](LICENSE.txt)
[![Packagist](https://img.shields.io/packagist/v/t3brightside/microstart.svg?style=flat)](https://packagist.org/packages/t3brightside/microstart)
[![Downloads](https://poser.pugx.org/t3brightside/microstart/downloads)](https://packagist.org/packages/t3brightside/microstart)
[![Brightside](https://img.shields.io/badge/by-t3brightside.com-orange.svg?style=flat)](https://t3brightside.com)

**Demo content for TYPO3 Microtemplate**

- **[Demo](https://microtemplate.t3brightside.com)**
- **[Microtemplate in TYPO3 Now Package](https://t3brightside.com/typo3-now)**

## Install
- install TYPO3 v12
- install microstart content and recommended packages by `composer req t3brightside/microstart`
- copy folders from vendor/t3brightside/microstart/data/fileadmin/ to public/fileadmin/
- import database from vendor/t3brightside/microstart/data/base.sql.gz
- back end admin user: **admin**, password: **Admin1234#**
- maintenance > analyze database structure
- add 'webp' to [GFX][imagefile_ext] and [SYS][mediafile_ext] in 'Settings > Configure Installation-Wide Options'
- in 'Settings > Extension Configuration > Pagelist' enable at least 'Articles' and 'Events' page types  and 'Personnel author fields' accordingly
- create a site configuration
- change the admin password as the first thing
- change the forms 'Contact Us' > 'Email to receiver' addresses and names to yours
- set route enhancers for pretty URL's in 'config/sites/your-site-name/confix.xml'
```yaml
routeEnhancers:
  PaginatedprocessorsByContentId:
    type: Simple
    routePath: '/{paginatorId}/{paginationPage}'
    aspects:
      paginatorId:
        type: PaginatedprocessorsContentMapper
      paginationPage:
        type: StaticRangeMapper
        start: '0'
        end: '999'
  PaginatedprocessorsByUnigueIdInTs:
    type: Simple
    routePath: '/{paginatorId}/{paginationPage}'
    aspects:
      paginatorId:
        type: StaticValueMapper
        map:
          files: files
          gallery: gallery
          pagelist: pagelist
      paginationPage:
        type: StaticRangeMapper
        start: '0'
        end: '999'
  PersonnelVcard:
    type: Simple
    routePath: '/{person}'
    defaults:
      tag: ''
    requirements:
      person: '[1-999]'
    _arguments:
      person: person
    aspects:
      person:
        type: StaticRangeMapper
        start: '1'
        end: '999'
  PageTypeSuffix:
    type: PageType
    map:
      vcard.vcf: 888
```

## Sources
- [GitHub](https://github.com/t3brightside/microstart)
- [Packagist](https://packagist.org/packages/t3brightside/microstart)

## Development and maintenance
[Brightside OÜ – TYPO3 development and hosting specialised web agency](https://t3brightside.com/)
