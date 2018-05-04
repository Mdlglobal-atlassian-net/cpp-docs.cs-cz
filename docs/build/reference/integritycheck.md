---
title: / INTEGRITYCHECK | Microsoft Docs
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
ms.openlocfilehash: 4b0adf9add2d191ae89aec0a5d756ade8e9f7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Určuje, že digitální podpis binární Image se musí kontrolovat v okamžiku načtení.

> **/ INTEGRITYCHECK**[**: NE**]

## <a name="remarks"></a>Poznámky

V záhlaví souboru DLL nebo spustitelný soubor tento parametr nastaví příznak, který vyžaduje kontrolu digitální podpis správce paměti se načíst obrázek v systému Windows. Verze Windows starší než Windows Vista Ignorovat tento příznak. Tato možnost musí být nastavena pro knihovny DLL 64-bit, které implementují kód režimu jádra a doporučuje se pro všechny ovladače zařízení. Další informace najdete v tématu [požadavky na podepisování kódu režimu jádra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)  
