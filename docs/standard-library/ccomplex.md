---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de5c67fc88da6fc4674b7dad67b5f74dcc3ce54d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850382"
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
