创建对于`crd`资源，自动创建`delpoy,svc,ingress`

### 下载安装

下载官方示例 `git clone git@github.com:kubernetes/sample-controller.git`

切换到对于k8s版本`git checkout v0.20.15`

修改`go.mod`项目名称，全局替换代码内的旧项目名称为新项目名称，项目名称和文件目录要一样，否则生成代码会不对

使用本地包 `go mod vendor`，删除久生成的代码`pkg/generated/`

修改`./hack/update-codegen.sh`中这行的内容` --output-base "$(dirname "${BASH_SOURCE[0]}")/../.."`

运行`./hack/update-codegen.sh`，查看是否能顺利生成

目前代码`tag:init`

编写完需求代码后，生成`crd`创建文件： `controller-gen crd paths=./... output:crd:dir=artifacts/crd`

创建`crd`:`kb apply -f artifacts/crd/samplecontroller.boyfoo.com_apps.yaml`

运行: `go run . --kubeconfig=/Users/rxt/.kube/config`


