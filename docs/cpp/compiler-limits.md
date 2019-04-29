---
title: Omezení kompilátoru
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: a0c6041d326982dc9807355733cf714dcfa62ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399158"
---
# <a name="compiler-limits"></a>Omezení kompilátoru

Standard jazyka C++ doporučuje limity pro různé jazykové konstrukce. Následuje seznam případů, kde kompilátor Visual C++ neimplementuje doporučené limity. První číslo je limit, který je vytvořen v normě ISO C++ 11 standard (INCITS/ISO/IEC 14882-2011 [2012], příloha B) a druhé číslo je limit implementovaný pomocí Visual C++:

- Vnořování úrovní složených příkazů, struktury řízení iterací a struktury řízení výběru - C++ standard: 256, vizuál C++ kompilátoru: závisí na kombinaci příkazů, které jsou vnořené, ale obecně rozsahu od 100 do 110.

- Parametry v jedné definici makra - C++ standard: 256, vizuál C++ kompilátoru: 127.

- Argumenty ve vyvolání jednoho makra - C++ standard: 256, vizuál C++ kompilátoru 127.

- Znaky v řetězec literálu nebo literál širokého řetězce (po zřetězení) - C++ standard: 65536, vizuál C++ kompilátoru: 65535 jednobajtové znaky, včetně ukončovacího znaku NULL a 32767 dvoubajtové znaky, včetně ukončovacího znaku NULL.

- Úrovně vnořené třídy, struktury nebo sjednocení definic v jednom `struct-declaration-list` - C++ standard: 256, vizuál C++ kompilátoru: 16.

- Inicializátoři členů v definici konstruktoru - C++ standard: 6144, vizuál C++ kompilátoru: nejméně 6144.

- Obor kvalifikaci jednoho identifikátoru - C++ standard: 256, vizuál C++ kompilátoru: 127.

- Vnořené **extern** specifikace - C++ standard: 1024, vizuál C++ kompilátoru: 9 (výčtu nebudou započteny implicitní **extern** specifikace v globálním oboru nebo 10, pokud počítáš implicitní **extern** specifikace v globálním oboru.

- Argumenty šablony v deklaraci šablony - C++ standard: 1024, vizuál C++ kompilátoru: 2046.

## <a name="see-also"></a>Viz také:

[Nestandardní chování](../cpp/nonstandard-behavior.md)