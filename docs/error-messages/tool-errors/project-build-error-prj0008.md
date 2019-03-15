---
title: Chyba sestavení projektu PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815993"
---
# <a name="project-build-error-prj0008"></a>Chyba sestavení projektu PRJ0008

Soubor 'file' se nepodařilo odstranit.

**Ujistěte se, že soubor není otevřen jiným procesem a že není chráněn proti zápisu.**

Během opětovné sestavení nebo vyčištění, odstraní všechny známé pomocných a výstupních souborů pro sestavení, stejně jako všechny soubory, které splňují na určení zástupných znaků ve Visual C++ **přípony odstraňované při čištění** vlastnost [obecné Stránka pro konfiguraci nastavení vlastností](../../build/reference/general-property-page-project.md).

Tato chyba se zobrazí, pokud není možné odstranit soubor jazyka Visual C++. Chcete-li vyřešit chybu, možnit souboru a jeho adresář pro uživatele provádějícího sestavení.