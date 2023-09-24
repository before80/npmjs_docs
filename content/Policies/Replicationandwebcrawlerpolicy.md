+++
title = "Replication and web crawler policy"
date = 2023-09-22T21:09:29+08:00
weight = 110
type = "docs"
description = ""
isCJKLanguage = true
draft = false
+++

> 原文: [https://docs.npmjs.com/policies/crawlers](https://docs.npmjs.com/policies/crawlers)

# Crawler policy - 爬虫政策

npm's full public dataset is available via the [public registry](https://docs.npmjs.com/misc/registry). Using CouchDB replication, you can get a full copy of all metadata, and it is acceptable within our terms of use to download copies of tarballs for inspection or experimentation.

​	npm的完整公共数据集可以通过[公共注册表](https://docs.npmjs.com/misc/registry)获得。使用CouchDB复制，您可以获得所有元数据的完整副本，并且在我们的使用条款内，可以下载tarball的副本进行检查或实验。

npm's [website](https://www.npmjs.com) also has package metadata available. We allow this content to be indexed by commercial crawlers such as GoogleBot. At our discretion, we also allow experimental crawlers to access the site, as long as they keep their request velocity to 1 request per second or less. At that velocity, indexing all packages would take 3 days, so if you want a full copy of our metadata it is always going to be faster to access the data via replication, which takes only an hour or two to provide full data and will thereafter automatically stay in sync.

​	npm的[网站](https://www.npmjs.com)上也提供软件包元数据。我们允许商业爬虫（如GoogleBot）索引这些内容。我们也允许实验性爬虫访问网站，但请求速度必须保持每秒1个请求或更低。以这个速度，索引所有软件包需要3天的时间，因此，如果您想要完整的元数据副本，最快的方式始终是通过复制访问数据，复制只需要1到2个小时即可提供完整的数据，并且随后会自动保持同步。

If you do not wish to install CouchDB to manage replication, we provide [open source software](https://github.com/npm/concurrent-couch-follower) that makes it easy to sync to the registry's public feed.

​	如果您不希望安装CouchDB来管理复制，我们提供了[开源软件](https://github.com/npm/concurrent-couch-follower)，使得与注册表的公共源进行同步变得容易。

If you attempt to access package metadata by high-velocity crawling of the npm website, we reserve the right to rate-limit or ban your IP, user-agent or both.

​	如果您尝试通过高速爬取npm网站来访问软件包元数据，我们保留限制您的IP、用户代理或两者的速率或禁止访问的权利。
