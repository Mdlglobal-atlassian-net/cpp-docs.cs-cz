---
title: / INTEGRITYCHECK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 062ce019fe1b622661be880d8a06eac9c5971103
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709200"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Určuje, že digitální podpis binárního obrazu musí být v okamžiku načtení zkontrolován.

> **/ INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Poznámky

V záhlaví souboru DLL nebo spustitelný soubor tento parametr nastaví příznak, který vyžaduje kontrolu digitálního podpisu správcem paměti k načtení obrázku v Windows. Verze Windows starší než Windows Vista ignorují tento příznak. Tato možnost musí být nastavena pro 64bitové knihovny DLL, které implementují kód režimu jádra a je doporučena pro všechny ovladače zařízení. Další informace najdete v tématu [požadavky pro podpis kódu režimu jádra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](../../build/reference/editbin-options.md)
