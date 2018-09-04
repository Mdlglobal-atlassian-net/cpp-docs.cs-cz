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
ms.openlocfilehash: 25ec172fb38fb3b200086c5f9317ccd8e5e54281
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691477"
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
|[basic_streambuf – třída](basic-streambuf-class.md)|Třída šablony popisuje abstraktní základní třída pro odvození vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z konkrétní reprezentace datového proudu.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
