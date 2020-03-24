---
title: Upozornění linkerů LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194275"
---
# <a name="linker-tools-warning-lnk4014"></a>Upozornění linkerů LNK4014

Nejde najít členský objekt ObjectName.

LIB nemůže najít `objectname` v knihovně.

Možnosti **/Remove** a **/Extract** vyžadují úplný název členského objektu, který má být odstraněn nebo zkopírován do souboru. Úplný název obsahuje cestu k původnímu souboru objektu. Chcete-li zobrazit úplné názvy členských objektů v knihovně, použijte DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) nebo lib [/list](../../build/reference/managing-a-library.md).
