---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 87fb74f62abffdd62b8c0179b13f53d96439d6c6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449567"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Zahrňte standardní hlavičku \<iostreams streambuf > k definování třídy template [basic_streambuf](../standard-library/basic-streambuf-class.md), která je základní pro provoz třídy iostreams. Tato hlavička je obvykle zahrnutá v jiné hlavičce iostreams; Jenom zřídka je potřeba ho zahrnout přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specializace `basic_streambuf` , která jako parametry šablony používá **char** .|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specializace `basic_streambuf` , která používá **wchar_t** jako parametry šablony.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_streambuf – třída](basic-streambuf-class.md)|Třída šablony popisuje abstraktní základní třídu pro odvození vyrovnávací paměti datového proudu, který řídí přenos prvků do a z konkrétní reprezentace datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
