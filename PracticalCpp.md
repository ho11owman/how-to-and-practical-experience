## transfer vector of pointers: Old Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

void old_style_impl(std::vector<int*>& v)
{
  for (int i = 0; i < v.size(); i++)
  {
    std::cout << v[i] << '\n';
    delete v[i];
  }
  v.clear();
}

void old_style()
{
  std::vector<int*> v;
  
  v.push_back(new int(2));
  v.push_back(new int(2));

  old_style_impl(v);
}

int main()
{
  old_style();
}
```

## transfer vector of shared pointers: New Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

class Data
{
public:
  Data()  { std::cout << "Construct" << '\n'; }
  ~Data() { std::cout << "Destruct" << '\n';  }

  void do_something() { std::cout << "do something" << '\n'; }
};

void new_style_impl(const std::vector<std::shared_ptr<Data>>& v)
{
  for (auto&& vit : v)
  {
    vit->do_something();
  }
}

void new_style()
{
  auto v = {
    std::make_shared<Data>(),
    std::make_shared<Data>()
  };
  new_style_impl(v);
  std::cout << "delete pointers" << '\n';
}

int main()
{
  new_style();
}
```

## transfer vector of unique pointers: New Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

class Data
{
public:
  Data()  { std::cout << "Construct" << '\n'; }
  ~Data() { std::cout << "Destruct" << '\n';  }

  void do_something() { std::cout << "do something" << '\n'; }
};

void new_style_impl(std::vector<std::unique_ptr<Data>> v) // atention: if set && then pointer not deleted hier
{
  for (auto&& vit : v)
  {
    vit->do_something();
  }
}

void new_style()
{
  std::vector<std::unique_ptr<Data>> v;
  
  v.push_back(std::make_unique<Data>());
  v.push_back(std::make_unique<Data>());

  new_style_impl(std::move(v));
  std::cout << "pointers deleted" << '\n';
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

std::vector<int*> old_style_impl()
{
  std::vector<int*> v;
  
  v.push_back(new int(2));
  v.push_back(new int(2));
  
  return v;
}

void old_style()
{
  std::vector<int*> v = old_style_impl();

  for (int i = 0; i < v.size(); i++)
  {
    std::cout << v[i] << '\n';
    delete v[i];
  }
}

int main()
{
  old_style();
}
```

## return vector of pointers: New Style c++

```c++
#include <vector>
#include <memory>
#include <iostream>

auto new_style_impl() -> std::vector<std::shared_ptr<int>>
{
  return {
    std::make_shared<int>(2),
    std::make_shared<int>(2)
  };
}

void new_style()
{
  auto v = new_style_impl();
  
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
