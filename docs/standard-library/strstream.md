---
title: '&lt;strstream –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f63ecc2f24431e54042a1b995762806f87c691da
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltstrstreamgt"></a>&lt;strstream –&gt;

Definuje několik tříd, které podporují operace iostreams v pořadí, které jsou uložené v přidělené pole `char` objektu. Takové pořadí se snadno převedou do a z řetězce C.

## <a name="syntax"></a>Syntaxe

```cpp
#include <strstream>

```

## <a name="remarks"></a>Poznámky

Objekty typu `strstream` práce s `char` *, které jsou řetězce, C. Použití [ \<sstream – >](../standard-library/sstream.md) pro práci s objekty typu [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Třídy v \<strstream – > jsou zastaralé. Zvažte použití třídy v \<sstream – > místo toho.

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[strstreambuf – třída](../standard-library/strstreambuf-class.md)|Třída popisuje datový proud vyrovnávací paměť, která řídí přenos elementů do a z pořadí prvků, které jsou uložené v `char` objekt array.|
|[istrstream – třída](../standard-library/istrstream-class.md)|Třída popisuje objekt, který řídí extrakce elementů a kódovaného objekty z datového proudu vyrovnávací paměti třídy [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream – třída](../standard-library/ostrstream-class.md)|Třída popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream – třída](../standard-library/strstream-class.md)|Třída popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [strstreambuf](../standard-library/strstreambuf-class.md).|

## <a name="see-also"></a>Viz také

[\<strstream – >](../standard-library/strstream.md)<br/>
[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
