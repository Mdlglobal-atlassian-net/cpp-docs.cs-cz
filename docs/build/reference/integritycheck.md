---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: b3f6622e3628db53c363b239c59accd94f708ab0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617267"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Určuje, že digitální podpis binárního obrazu musí být v okamžiku načtení zkontrolován.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Poznámky

V záhlaví souboru DLL nebo spustitelný soubor tento parametr nastaví příznak, který vyžaduje kontrolu digitálního podpisu správcem paměti k načtení obrázku v Windows. Verze Windows starší než Windows Vista ignorují tento příznak. Tato možnost musí být nastavena pro 64bitové knihovny DLL, které implementují kód režimu jádra a je doporučena pro všechny ovladače zařízení. Další informace najdete v tématu [požadavky pro podpis kódu režimu jádra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](../../build/reference/editbin-options.md)
