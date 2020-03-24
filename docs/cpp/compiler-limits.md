---
title: Omezení kompilátoru
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189573"
---
# <a name="compiler-limits"></a>Omezení kompilátoru

Standard jazyka C++ doporučuje limity pro různé jazykové konstrukce. V následujícím seznamu jsou uvedeny případy, kdy kompilátor společnosti C++ Microsoft neimplementuje doporučená omezení. První číslo je limit, který je stanoven v normě ISO C++ 11 (INCITS/ISO/IEC 14882-2011 [2012], příloha B) a druhým číslem je limit implementovaný kompilátorem Microsoftu C++ :

- Vnořování úrovní složených příkazů, struktur ovládacích prvků iterací a struktur ovládacích prvků výběru – C++ standard: 256, Microsoft C++ Compiler: závisí na kombinaci příkazů, které jsou vnořené, ale obvykle mezi 100 a 110.

- Parametry v jedné definici makra C++ standard: 256, Microsoft C++ Compiler: 127.

- Argumenty v jednom volání makra – C++ standard: 256, Microsoft C++ Compiler 127.

- Znaky v řetězcovém literálu znaků nebo textový literál typu řetězec (po zřetězení C++ ) – standard: 65536 C++ , Microsoft Compiler: 65535 jednobajtových znaků, včetně ukončovacího znaku null, a 32767 dvoubajtové znaky, včetně ukončovacího znaku null.

- Úrovně vnořených definic třídy, struktury nebo sjednocení v jednom `struct-declaration-list` – C++ standard: 256, Microsoft C++ Compiler: 16.

- Inicializátory členů v definici konstruktoru – C++ standard: 6144, Microsoft C++ Compiler: aspoň 6144.

- Kvalifikace oboru jednoho identifikátoru C++ standard: 256, Microsoft C++ Compiler: 127.

- Vnořené specifikace **extern** – C++ Standard: 1024, Microsoft C++ Compiler: 9 (nepočítají se implicitní **externí** specifikace v globálním oboru nebo 10, pokud chcete spočítat implicitní **externí** specifikaci v globálním oboru..

- Argumenty šablony v deklaraci šablony – C++ standard: 1024, Microsoft C++ Compiler: 2046.

## <a name="see-also"></a>Viz také

[Nestandardní chování](../cpp/nonstandard-behavior.md)
