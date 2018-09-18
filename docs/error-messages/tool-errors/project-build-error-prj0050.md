---
title: Chyba sestavení projektu PRJ0050 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb3949ea0db2f1667aecf1aeeefd922b192cbf41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100588"
---
# <a name="project-build-error-prj0050"></a>Chyba sestavení projektu PRJ0050

Registrace výstupu se nezdařila. Ujistěte se prosím, že máte příslušná oprávnění k úpravám registru.

Systém sestavení Visual C++ nebyl schopen registrovat výstup sestavení (knihovna dll nebo .exe). Musíte být přihlášeni jako správce k úpravám registru.

Pokud vytváříte soubor .dll, můžete se pokusit zaregistrovat ručně pomocí regsvr32.exe soubor .dll, mělo by se zobrazit informace o sestavení o příčině selhání.

Pokud vytváříte nejsou ve formátu .dll, podívejte se na příkaz, který způsobí chybu v protokolu sestavení.