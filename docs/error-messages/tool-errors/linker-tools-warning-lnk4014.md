---
title: Upozornění linkerů LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: f67990ed74f500f1b954edcf1d6437f64f93f0d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298604"
---
# <a name="linker-tools-warning-lnk4014"></a>Upozornění linkerů LNK4014

nejde najít členský objekt "objectname"

Nelze najít LIB `objectname` v knihovně.

**/REMOVE** a **/EXTRAHOVAT** možnosti vyžadují celý název člena objektu, který je odstraněn, nebo se zkopíruje do souboru. Úplný název obsahuje cestu k souboru původní objekt. Chcete-li zobrazit úplné názvy členské objekty v knihovně, použijte DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) nebo LIB [/LIST](../../build/reference/managing-a-library.md).