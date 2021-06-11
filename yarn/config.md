#### 安装

```
npm install -g yarn
```

#### 修改路径 

##### 改变bin路径

```
yarn config set prefix "D:\software\Yarn\Data"
```

##### 改变全局安装位置

```
yarn config  set global-folder "D:\software\Yarn\Data\global"

```

##### 改变缓存位置 

```
yarn config set cache-folder "D:\software\Yarn\Cache"
```

##### 改变link位置

```
yarn config set link-folder "D:\software\Yarn\Data\link"
```

#### 查看路径 

##### bin路径

```
yarn global bin
```

##### 依赖路径 

```
yarn global dir
```

##### 缓存位置 

```
yarn cache dir
```

