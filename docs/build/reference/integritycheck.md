---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269762"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Určuje, že digitální podpis binárního obrazu musí být v okamžiku načtení zkontrolován.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Poznámky

V záhlaví souboru DLL nebo spustitelný soubor tento parametr nastaví příznak, který vyžaduje kontrolu digitálního podpisu správcem paměti k načtení obrázku v Windows. Verze Windows starší než Windows Vista ignorují tento příznak. Tato možnost musí být nastavena pro 64bitové knihovny DLL, které implementují kód režimu jádra a je doporučena pro všechny ovladače zařízení. Další informace najdete v tématu [požadavky pro podpis kódu režimu jádra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)
