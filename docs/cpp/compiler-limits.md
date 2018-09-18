---
title: Omezení kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76b08ab88ce5487485c8b8872488c0cf784ad2c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093542"
---
# <a name="compiler-limits"></a>Omezení kompilátoru

Standard jazyka C++ doporučuje limity pro různé jazykové konstrukce. Následuje seznam případů, kde kompilátor Visual C++ neimplementuje doporučené limity. První číslo je limit, který je vytvořen ISO C++ 11 standard (INCITS/ISO/IEC 14882-2011 [2012], příloha B) a druhé číslo je limit implementovaný pomocí Visual C++:

- Vnořování úrovní složených příkazů, struktury řízení iterací a výběr řízení struktury – C++ standard: 256, kompilátor Visual C++: závisí na kombinaci příkazů, které jsou vnořené, ale obecně rozsahu od 100 do 110.

- Parametry v jedné definici makra – C++ standard: 256, kompilátor Visual C++: 127.

- Argumenty ve vyvolání jednoho makra – C++ standard: 256, kompilátor Visual C++ 127.

- Znaky v řetězec literálu nebo literál širokého řetězce (po zřetězení) – standard jazyka C++: 65536, kompilátor Visual C++: 65535 jednobajtové znaky, včetně ukončovacího znaku NULL a 32767 dvoubajtové znaky, včetně ukončovacího znaku NULL.

- Úrovně vnořené třídy, struktury nebo sjednocení definic v jednom `struct-declaration-list` – standard jazyka C++: 256, kompilátor Visual C++: 16.

- Inicializátoři členů v definici konstruktoru – C++ standard: 6144, kompilátor Visual C++: nejméně 6144.

- Určení rozsahu jednoho identifikátoru – C++ standard kvalifikací: 256, kompilátor Visual C++: 127.

- Vnořené **extern** specifikace – C++ standard: 1024, kompilátor Visual C++: 9 (nepočítají implicitní **extern** specifikace v globálním oboru nebo 10, pokud počítáš implicitní **extern**  specifikace v globálním oboru...

- Argumenty šablony v deklaraci šablony – C++ standard: 1024, kompilátor Visual C++: 2046.

## <a name="see-also"></a>Viz také:

[Nestandardní chování](../cpp/nonstandard-behavior.md)