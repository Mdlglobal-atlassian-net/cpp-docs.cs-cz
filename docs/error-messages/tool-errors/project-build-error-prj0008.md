---
title: Chyba sestavení projektu PRJ0008 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0008
dev_langs:
- C++
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7c24634a845423de590228af01cb9f4779e37ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062784"
---
# <a name="project-build-error-prj0008"></a>Chyba sestavení projektu PRJ0008

Soubor 'file' se nepodařilo odstranit.

**Ujistěte se, že soubor není otevřen jiným procesem a že není chráněn proti zápisu.**

Během opětovné sestavení nebo vyčištění, odstraní všechny známé pomocných a výstupních souborů pro sestavení, stejně jako všechny soubory, které splňují na určení zástupných znaků ve Visual C++ **přípony odstraňované při čištění** vlastnost [obecné Stránka pro konfiguraci nastavení vlastností](../../ide/general-property-page-project.md).

Tato chyba se zobrazí, pokud není možné odstranit soubor jazyka Visual C++. Chcete-li vyřešit chybu, možnit souboru a jeho adresář pro uživatele provádějícího sestavení.