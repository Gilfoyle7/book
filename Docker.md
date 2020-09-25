##Docker容器卷

docker 为我们提供了三种不同的方式将数据挂载到容器中：volume、bind mount、`tmpfs`。

###volume方式

volume 方式是 docker 中数据持久化的最佳方式。

- docker 默认在主机上会有一个特定的区域（`/var/lib/docker/volumes/` Linux），该区域用来存放 volume。
- 非 docker 进程不应该去修改该区域。
- volume 可以通过 `docker volume` 进行管理，如创建、删除等操作。
- volume 在生成的时候如果不指定名称，便会随机生成。

- volume 在容器停止或删除的时候会继续存在，如需删除需要显示声明。

>$ docker rm -v <container_id>
>$ docker volume rm <volume_name>

####相关用例

volume 方式应该是持久化数据的首选方式， 其推荐用例：

- 在多个容器之间共享数据，volume 在容器停止或删除的时候依然存在，如果需要删除需要显示（docker rm -v…），多个容器可以加载相同的卷。
- 当主机不能保证有一个指定的目录或文件结构时。
- 当需要备份、还原或主机间的数据迁移时。停止容器，备份卷的目录（如`/var/lib/docker/volumes/<volume-name>`。

如何选择-v或者--mount

两者的区别在于，`-v` 将所有选项组合在一个字段中，`--mount` 则将它们分开。

> 新用户应该尝试--mount语法，它比--volume语法更简单。

####-v和-mount