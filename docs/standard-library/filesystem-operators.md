---
title: '&lt;FileSystem&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 546e601afeb05e0347dba8bf792611f20068c69b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ltfilesystemgt-operators"></a>&lt;FileSystem&gt; operátory

Operátory, proveďte lexikální porovnání dvě cesty řetězce. Použití **ekvivalentní** funkce k určení, zda dvě cesty (například relativní cesty a absolutní cesta) odkazovat na stejný soubor nebo adresář na disku.

Další informace najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

Funkce vrátí hodnotu left.native() == right.native().

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

Funkce vrátí hodnotu! (vlevo == vpravo).

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

Funkce vrátí hodnotu left.native() < right.native().

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

Funkce vrátí hodnotu! (vpravo \< levém).

## <a name="operator"></a>operátor >

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

Funkce vrátí hodnotu právo \< levé.

## <a name="operator"></a>Operator > =

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

Funkce vrátí hodnotu! (levém < vpravo).

## <a name="operator"></a>operátor nebo

```cpp
path operator/(const path& left, const path& right);
```

Provede funkci:

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

Funkce vrátí hodnotu os << pval.string\<Elem, vlastnosti > ().

## <a name="operator"></a>operátor >>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

Provede funkci:

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```

## <a name="see-also"></a>Viz také

[Path – třída (standardní knihovna C++)](../standard-library/path-class.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
