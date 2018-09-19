---
title: TypeName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77e3cc6f9691cf071a420ee2659c713f9e28036f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061588"
---
# <a name="typename"></a>typename

V definicích šablon poskytuje nápovědu pro kompilátor, že neznámý identifikátor je typ. V seznamech parametrů šablony slouží k určení typu parametru.

## <a name="syntax"></a>Syntaxe

```
typename identifier;
```

## <a name="remarks"></a>Poznámky

Toto klíčové slovo musí použít, pokud kvalifikovaný název, který je závislý na argumentu šablony; je název v definici šablony je volitelný, pokud kvalifikovaný název není závislý. Další informace najdete v tématu [šablony a rozlišení názvů](../cpp/templates-and-name-resolution.md).

**TypeName** mohou využívat libovolným typem kdekoli v deklaraci šablony nebo definice. Není povoleno v seznamu základních tříd, nejde-li o argument šablony základní třídy šablony.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**Typename** – klíčové slovo lze také místo **třídy** v seznamech parametrů šablony. Například následující příkazy jsou sémanticky ekvivalentní:

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

## <a name="see-also"></a>Viz také:

[Šablony](../cpp/templates-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)