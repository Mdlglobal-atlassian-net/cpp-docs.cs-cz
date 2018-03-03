---
title: / INTEGRITYCHECK | Microsoft Docs
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99caec18162a7506b8b7a467eb7374b6fe4a38d9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Určuje, že digitální podpis binární Image se musí kontrolovat v okamžiku načtení.

> **/ INTEGRITYCHECK**[**: NE**]

## <a name="remarks"></a>Poznámky

V záhlaví souboru DLL nebo spustitelný soubor tento parametr nastaví příznak, který vyžaduje kontrolu digitální podpis správce paměti se načíst obrázek v systému Windows. Verze Windows starší než Windows Vista Ignorovat tento příznak. Tato možnost musí být nastavena pro knihovny DLL 64-bit, které implementují kód režimu jádra a doporučuje se pro všechny ovladače zařízení. Další informace najdete v tématu [požadavky na podepisování kódu režimu jádra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)  
