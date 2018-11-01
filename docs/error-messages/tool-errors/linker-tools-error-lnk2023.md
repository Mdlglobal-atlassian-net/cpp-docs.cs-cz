---
title: Chyba linkerů LNK2023
ms.date: 11/04/2016
f1_keywords:
- LNK2023
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
ms.openlocfilehash: c5bc70aeb3a7e39bc60bb745060e7a5740ad7a28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658689"
---
# <a name="linker-tools-error-lnk2023"></a>Chyba linkerů LNK2023

Chybná knihovna dll nebo vstupní bod \<knihovna dll nebo vstupní bod >

Linker se načítá nesprávná verze msobj90.dll. Zajistěte, aby link.exe a msobj90.dll ve své cestě měly stejnou verzi.

Závislost msobj90.dll nemusí být k dispozici. Seznam závislostí pro msobj90.dll je:

- Msvcr90.dll

- Kernel32.dll

Zkontrolujte váš počítač pro všechny ostatní kopie msobj90.dll, který může být zastaralá.