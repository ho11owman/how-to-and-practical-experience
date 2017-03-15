## transfer vector of pointers: Old Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

void old_stype_impl(std::vector<int*>& v)
{
  for (int i = 0; i < v.size(); i++)
  {
    std::cout << v[i] << '\n';
    delete v[i];
  }
  v.clear();
}

void old_stype()
{
  std::vector<int*> v;
  
  v.push_back(new int(2));
  v.push_back(new int(2));

  old_stype_impl(v);
}

int main()
{
  old_stype();
}
```

## transfer vector of pointers: New Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

void new_stype_impl(std::vector<std::shared_ptr<int>> v)
{
  for (auto vit : v)
  {
    std::cout << *vit << '\n';
  }
}

void new_style()
{
  auto v = {
    std::make_shared<int>(2),
    std::make_shared<int>(2)
  };
  new_stype_impl(std::move(v));
}

int main()
{
  new_style();
}
```

## return vector of pointers: Old Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

std::vector<int*> old_stype_impl()
{
  std::vector<int*> v;
  
  v.push_back(new int(2));
  v.push_back(new int(2));
  
  return v;
}

void old_stype()
{
  std::vector<int*> v = old_stype_impl();

  for (int i = 0; i < v.size(); i++)
  {
    std::cout << v[i] << '\n';
    delete v[i];
  }
}

int main()
{
  old_stype();
}
```

## return vector of pointers: New Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

auto new_stype_impl() -> std::vector<std::shared_ptr<int>>
{
  return {
    std::make_shared<int>(2),
    std::make_shared<int>(2)
  };
}

void new_style()
{
  auto v = new_stype_impl();
  
  for (auto vit : v)
  {
    std::cout << *vit << '\n';
  }
}

int main()
{
  new_style();
}
```
