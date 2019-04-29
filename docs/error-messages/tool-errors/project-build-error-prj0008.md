---
title: Chyba sestavení projektu PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 5741b7ef8cb9a7ae53d64874d3531e9271c09e0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359485"
---
# <a name="project-build-error-prj0008"></a>Chyba sestavení projektu PRJ0008

Soubor 'file' se nepodařilo odstranit.

**Ujistěte se, že soubor není otevřen jiným procesem a že není chráněn proti zápisu.**

Během opětovné sestavení nebo vyčištění, odstraní všechny známé pomocných a výstupních souborů pro sestavení, stejně jako všechny soubory, které splňují na určení zástupných znaků ve Visual C++ **přípony odstraňované při čištění** vlastnost [obecné Stránka pro konfiguraci nastavení vlastností](../../build/reference/general-property-page-project.md).

Tato chyba se zobrazí, pokud není možné odstranit soubor jazyka Visual C++. Chcete-li vyřešit chybu, možnit souboru a jeho adresář pro uživatele provádějícího sestavení.