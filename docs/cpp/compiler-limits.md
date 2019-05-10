---
title: Omezení kompilátoru
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9663da06c97886ef1cd20ca2928944795b39dc18
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222203"
---
# <a name="compiler-limits"></a>Omezení kompilátoru

Standard jazyka C++ doporučuje limity pro různé jazykové konstrukce. Tady je seznam případů, kdy Microsoft C++ kompilátoru neimplementuje doporučené limity. První číslo je limit, který je vytvořen v normě ISO C++ 11 standard (INCITS/ISO/IEC 14882-2011 [2012], příloha B) a druhé číslo je limit implementovaný pomocí Microsoft C++ kompilátoru:

- Vnořování úrovní složených příkazů, struktury řízení iterací a struktury řízení výběru - C++ standard: 256, Microsoft C++ kompilátoru: závisí na kombinaci příkazů, které jsou vnořené, ale obecně rozsahu od 100 do 110.

- Parametry v jedné definici makra - C++ standard: 256, Microsoft C++ kompilátoru: 127.

- Argumenty ve vyvolání jednoho makra - C++ standard: 256, Microsoft C++ kompilátoru 127.

- Znaky v řetězec literálu nebo literál širokého řetězce (po zřetězení) - C++ standard: 65536, Microsoft C++ kompilátoru: 65535 jednobajtové znaky, včetně ukončovacího znaku NULL a 32767 dvoubajtové znaky, včetně ukončovacího znaku NULL.

- Úrovně vnořené třídy, struktury nebo sjednocení definic v jednom `struct-declaration-list` - C++ standard: 256, Microsoft C++ kompilátoru: 16.

- Inicializátoři členů v definici konstruktoru - C++ standard: 6144, Microsoft C++ kompilátoru: nejméně 6144.

- Obor kvalifikaci jednoho identifikátoru - C++ standard: 256, Microsoft C++ kompilátoru: 127.

- Vnořené **extern** specifikace - C++ standard: 1024, Microsoft C++ kompilátoru: 9 (výčtu nebudou započteny implicitní **extern** specifikace v globálním oboru nebo 10, pokud počítáš implicitní **extern** specifikace v globálním oboru.

- Argumenty šablony v deklaraci šablony - C++ standard: 1024, Microsoft C++ kompilátoru: 2046.

## <a name="see-also"></a>Viz také:

[Nestandardní chování](../cpp/nonstandard-behavior.md)