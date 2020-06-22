# 时间复杂度和空间复杂度

## 常用的时间复杂度的量级

常数阶O\(1\)

平方阶O\(n^2\)

线性阶O\(n\)

对数阶O\(logN\)

线性对数阶O\(nlogN\)

立方阶O\(n^3\)

### O\(nlogN\)

```text
for(let i=0;i<n;i++){
    let x = 1;
    while(x < n){
        x = x * 2;
    }
}
```

### O\(n^2\)

```text
for(let i=1;i<n;i++){
    for(let j=1;j<n;j++){
        x++
    }
}
```

## 空间常用复杂度的量级

O\(1\)

O\(n\)

O\(n^2\)

