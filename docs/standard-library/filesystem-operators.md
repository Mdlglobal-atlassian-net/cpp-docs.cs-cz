---
title: '&lt;systém souborů&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
ms.openlocfilehash: 378e5d7b8b36aa9b891a87662d432a451ac6bafe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631016"
---
# <a name="ltfilesystemgt-operators"></a>&lt;systém souborů&gt; operátory

Operátory provést lexikální porovnání ze dvou možných cest jako řetězce. Použití `equivalent` funkce k určení, zda dvě cesty (například relativní cesty a absolutní cesta) odkazují na stejný soubor nebo adresář na disku.

Další informace najdete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

Funkce vrátí left.native() == right.native().

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

Funkce vrátí! (== zleva doprava).

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

Funkce vrátí left.native() < right.native().

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

Funkce vrátí! (pravém \< vlevo).

## <a name="operator"></a>Operator >

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

Funkce vrátí přímo \< vlevo.

## <a name="operator"></a>Operator > =

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

Funkce vrátí! (levý < vpravo).

## <a name="operator"></a>Operator /

```cpp
path operator/(const path& left, const path& right);
```

Provede se příslušná funkce:

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a>operátor <<

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

Funkce vrátí os << pval.string\<Elem, osobnostní rysy > ().

## <a name="operator"></a>operátor >>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

Provede se příslušná funkce:

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```

## <a name="see-also"></a>Viz také:

[Path – třída (standardní knihovna C++)](../standard-library/path-class.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
