---
title: '&lt;streambuf –&gt; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <streambuf>
dev_langs:
- C++
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db05d1b19a67fc54a148d407fd90992a6d37c4c6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213584"
---
# <a name="ltstreambufgt"></a>&lt;streambuf –&gt;

Zahrnout standardní hlavička iostreams \<streambuf – > k definování šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), což je základní operace třídami iostreams. Tato hlavička se obvykle zahrnuté pro vás jiná záhlaví iostreams; je potřeba jen zřídka zahrnují přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <streambuf>

```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[streambuf –](../standard-library/streambuf-typedefs.md#streambuf)|Specializace `basic_streambuf` , která používá **char** jako parametry šablony.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specializace `basic_streambuf` , která používá **wchar_t** jako parametry šablony.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_streambuf – třída](https://msdn.microsoft.com/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|Třída šablony popisuje abstraktní základní třída pro odvození vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z konkrétní reprezentace datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
