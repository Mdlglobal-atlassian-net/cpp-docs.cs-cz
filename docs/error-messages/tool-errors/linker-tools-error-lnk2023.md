---
title: Chyba Linkerů LNK2023 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d8deaf8bfb10d3ceb56380560320ebb2cf9a7b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090318"
---
# <a name="linker-tools-error-lnk2023"></a>Chyba linkerů LNK2023

Chybná knihovna dll nebo vstupní bod \<knihovna dll nebo vstupní bod >

Linker se načítá nesprávná verze msobj90.dll. Zajistěte, aby link.exe a msobj90.dll ve své cestě měly stejnou verzi.

Závislost msobj90.dll nemusí být k dispozici. Seznam závislostí pro msobj90.dll je:

- Msvcr90.dll

- Kernel32.dll

Zkontrolujte váš počítač pro všechny ostatní kopie msobj90.dll, který může být zastaralá.