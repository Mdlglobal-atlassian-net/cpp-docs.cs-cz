---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea7ffa0db396242ab072efd01ccdd3def75fea9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Obsahuje hlavičku standardní knihovna C++ [ \<komplexní >](../standard-library/complex.md), což zahrnuje efektivně hlavičku knihovny standardní C \<complex.h > a přidá přidružené jména `std` obor názvů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ccomplex>

```

## <a name="remarks"></a>Poznámky

Včetně tuto hlavičku zajistí, že jsou názvy deklarováno s použitím externí propojení v hlavičce knihovny standardní C deklarované v `std` oboru názvů.

Název `clog`, kterého je deklarovaná v \<complex.h >, není definován v `std` obor názvů kvůli možným konfliktům s `clog` deklarovaného v souboru [ \<iostream >](../standard-library/iostream.md).

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
