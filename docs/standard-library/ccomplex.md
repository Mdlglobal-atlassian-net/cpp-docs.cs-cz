---
title: '&lt;ccomplex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ccomplex>
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: e0f8c31afac0608b4de66bd10602264666d39426
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667932"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Obsahuje hlavičku standardní knihovny C++ [ \<komplexní >](../standard-library/complex.md), která ve skutečnosti obsahuje hlavičku knihovny Standard C \<complex.h > a přidá názvy přidružené k `std` oboru názvů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ccomplex>

```

## <a name="remarks"></a>Poznámky

Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v záhlaví knihovny Standard C jsou deklarovány v `std` oboru názvů.

Název `clog`, který je deklarován v \<complex.h >, není definována v `std` obor názvů kvůli možným konfliktům s `clog` , která je deklarována v [ \<iostream – >](../standard-library/iostream.md).

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
