---
title: Ladění a naslouchání vloženého sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 457402626edcdb2be05923aa33bbd26b1cab7137
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050113"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Ladění a naslouchání vloženého sestavení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Programy obsahující kódu vnořeného sestavení můžete ladit pomocí ladicího programu úrovně zdroje, když kompilujete s [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost.  
  
 V ladicím programu můžete nastavit zarážky na řádky C nebo C++ a jazyk sestavení. Pokud povolíte smíšená sestavení a zdroj režimu, můžete zobrazit zdroj a bylo formu kódu sestavení.  
  
 Všimněte si, že uvedení na jednom řádku více sestavení pokyny nebo příkazy jazyka zdroje může zabránit spuštění ladění. V režimu zdroje můžete nastavit zarážky na jeden řádek, ale nikoli na jednotlivé příkazy na stejném řádku ladicího programu. Stejný princip platí pro `__asm` bloku definován jako makro C, které zasahuje do jednoho logického řádku.  
  
 Pokud vytvoříte smíšený zdroje a zobrazení seznamu pomocí sestavení [/FAs](../../build/reference/fa-fa-listing-file.md) – možnost kompilátoru, seznam obsahuje jak zdrojové, tak sestavení formuláře každého symbolické řádku. Makra nejsou rozšířit ve výpisech, ale jsou rozšířit během kompilace.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)