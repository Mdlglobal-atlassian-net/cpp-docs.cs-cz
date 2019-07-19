---
title: '&lt;ccomplex&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ccomplex>
- ccomplex
helpviewer_keywords:
- ccomplex header
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: 5b5383b1eca4fda72f5f9e3a78637373acbcf7ab
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341139"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

Zahrnuje C++ standardní [ \<>](complex.md)hlaviček standardní knihovny.

> [!NOTE]
> \<Standardní knihovna C složitá. h > hlavička není \<součástí ccomplex >, protože je účinně nahrazena C++ přetíženími v \<komplexním > a \<cmath >. Tím se \<ccomplex > redundantní záhlaví. Hlavička Complex. h > je zastaralá v C++ \< Hlavička \<> ccomplex je v c++ 17 zastaralá a odebrala se v konceptu c++ 20 Standard.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<ccomplex >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Název `clog`, který je deklarován v \<Complex. h > `std` , není definován v oboru názvů z důvodu potenciálních konfliktů s `clog` deklarací, která je deklarována v [ \<iostream – >](iostream.md).

## <a name="see-also"></a>Viz také:

[\<komplexní >](complex.md)\
[\<cmath>](cmath.md)\
[Odkazy na hlavičkové soubory](cpp-standard-library-header-files.md)\
[C++Přehled standardní knihovny](cpp-standard-library-overview.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](thread-safety-in-the-cpp-standard-library.md)
