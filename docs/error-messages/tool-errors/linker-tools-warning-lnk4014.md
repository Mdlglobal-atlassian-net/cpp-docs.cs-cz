---
title: Upozornění Linkerů LNK4014 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df0a3b6f30733413a0f27c0b8daa07394bb04b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023108"
---
# <a name="linker-tools-warning-lnk4014"></a>Upozornění linkerů LNK4014

nejde najít členský objekt "objectname"

Nelze najít LIB `objectname` v knihovně.

**/REMOVE** a **/EXTRAHOVAT** možnosti vyžadují celý název člena objektu, který je odstraněn, nebo se zkopíruje do souboru. Úplný název obsahuje cestu k souboru původní objekt. Chcete-li zobrazit úplné názvy členské objekty v knihovně, použijte DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) nebo LIB [/LIST](../../build/reference/managing-a-library.md).