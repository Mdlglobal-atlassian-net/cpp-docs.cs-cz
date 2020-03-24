---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 789bb879922bbd96a04085159205d02fb7f495c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160681"
---
# <a name="typename"></a>typename

V definicích šablon poskytuje nápovědu pro kompilátor, že neznámý identifikátor je typ. V seznamech parametrů šablony se používá k určení parametru typu.

## <a name="syntax"></a>Syntaxe

```
typename identifier;
```

## <a name="remarks"></a>Poznámky

Toto klíčové slovo musí být použito, je-li název v definici šablony kvalifikovaný název, který je závislý na argumentu šablony. je volitelné, pokud kvalifikovaný název není závislý. Další informace najdete v tématu [šablony a překlad názvů](../cpp/templates-and-name-resolution.md).

**TypeName** lze použít libovolného typu kdekoli v deklaraci nebo definici šablony. Není povoleno v seznamu základních tříd, nejde-li o argument šablony základní třídy šablony.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

Klíčové slovo **TypeName** lze také použít místo **třídy** v seznamech parametrů šablony. Například následující příkazy jsou sémanticky ekvivalentní:

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>Příklad

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>Viz také

[Šablony](../cpp/templates-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
