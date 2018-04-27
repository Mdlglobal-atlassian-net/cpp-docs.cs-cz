---
title: '&lt;streambuf –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <streambuf>
dev_langs:
- C++
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84b8e370da8e717e7d941cbae8de0637d1eb74da
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltstreambufgt"></a>&lt;streambuf –&gt;

Zahrnují standardní hlavičku iostreams \<streambuf – > definovat šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), což je základní operace iostreams třídy. Tuto hlavičku je obvykle zahrnuté pro vás jiným hlaviček iostreams; je potřeba jen zřídka ho zahrňte přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <streambuf>

```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[streambuf –](../standard-library/streambuf-typedefs.md#streambuf)|Specializace z `basic_streambuf` používající `char` jako parametry šablony.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Specializace z `basic_streambuf` používající `wchar_t` jako parametry šablony.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_streambuf – třída](http://msdn.microsoft.com/en-us/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|Šablony třídy popisuje abstraktní základní třídu pro odvození datového proudu vyrovnávací paměti řídí přenos elementů do a z konkrétní reprezentace datového proudu.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
