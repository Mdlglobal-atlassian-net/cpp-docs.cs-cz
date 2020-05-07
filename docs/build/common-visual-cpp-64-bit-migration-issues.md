---
title: Obecné problémy migrace v 64bitovém prostředí Visual C++
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 004fe7ace6102feecbcb2f542b5b93268ae2f868
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493317"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Obecné problémy migrace v 64bitovém prostředí Visual C++

Když použijete kompilátor Microsoft C++ (MSVC) k vytváření aplikací, které se mají spouštět na 64 operačním systému Windows, měli byste si uvědomit následující problémy:

- `int` A a `long` jsou 32 hodnoty na 64 operačních systémech Windows. Pro programy, které plánujete kompilovat pro 64 platformy, byste měli být opatrní, abyste nepřiřadili ukazatelům ke 32 bitovým proměnným. Ukazatele jsou 64-bit na 64 platformách a hodnota ukazatele se zkrátí, pokud ji přiřadíte proměnné 32-bit.

- `size_t`, `time_t`a `ptrdiff_t` jsou 64 hodnoty na 64 operačních systémů Windows.

- `time_t`je 32 hodnota v 32 operačních systémech Windows v aplikaci Visual Studio 2005 a starších verzích. `time_t`ve výchozím nastavení je teď 64 celé číslo. Další informace najdete v tématu [Správa času](../c-runtime-library/time-management.md).

   Měli byste vědět, kde kód přebírá `int` hodnotu a zpracovává ho jako hodnotu `size_t` nebo. `time_t` Je možné, že počet může být větší než 32-bit a data se při předání zpátky do `int` úložiště zkrátí.

Modifikátor% x (šestnáctkový `int` formát `printf` ) nebude fungovat podle očekávání v operačním systému Windows 64. Bude fungovat pouze v prvních 32 bitech hodnoty, která je předána.

- Pomocí% I32x můžete zobrazit 32 integrálový typ v šestnáctkovém formátu.

- Pomocí% I64x můžete zobrazit 64 integrálový typ v šestnáctkovém formátu.

- % P (šestnáctkový formát pro ukazatel) bude v operačním systému Windows 64 fungovat podle očekávání.

Další informace naleznete v tématu:

- [Parametry kompilátoru MSVC](reference/compiler-options.md)

- [Tipy k migraci](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>Viz také

[Konfigurace projektů C++ pro 64 cíle platformy x64](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Průvodce přenosem a upgradem Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
