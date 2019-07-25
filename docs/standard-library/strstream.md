---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: ecf8499a07f03c00588e7b7fd83b8d41a23e8e7a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459089"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Definuje několik tříd, které podporují operace iostreams na sekvencích uložených v přiděleném poli objektu **char** . Tyto sekvence jsou snadno převedeny na řetězce C a z nich.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<strstream >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Objekty typu `strstream` Work fungují s `char` *, což jsou řetězce jazyka C. [ Použijte\<sstream >](../standard-library/sstream.md) pro práci s objekty typu [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Třídy v \<> strstream jsou zastaralé. Místo toho zvažte použití tříd \<v sstream >.

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[strstreambuf – třída](../standard-library/strstreambuf-class.md)|Třída popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků do a z sekvence prvků uložených v objektu Array typu **char** .|
|[istrstream – třída](../standard-library/istrstream-class.md)|Třída popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream – třída](../standard-library/ostrstream-class.md)|Třída popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream – třída](../standard-library/strstream-class.md)|Třída popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Funkce

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Viz také:

[\<strstream >](../standard-library/strstream.md)\
[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
