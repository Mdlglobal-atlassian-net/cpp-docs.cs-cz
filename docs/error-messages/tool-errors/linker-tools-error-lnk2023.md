---
title: Chyba linkerů LNK2023
ms.date: 11/04/2016
f1_keywords:
- LNK2023
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
ms.openlocfilehash: 363b6ef0ea9991ff5d657044282e99c558257fb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194626"
---
# <a name="linker-tools-error-lnk2023"></a>Chyba linkerů LNK2023

Chybná knihovna DLL nebo vstupní bod \<DLL nebo vstupní bod >

Linker načítá nesprávnou verzi msobj90. dll. Zajistěte, aby v cestě Link. exe a msobj90. dll měla stejnou verzi.

Nemusí být k dispozici závislost msobj90. dll. Seznam závislostí pro msobj90. dll je:

- Msvcr90.dll

- Kernel32.dll

Ověřte si počítač pro všechny ostatní kopie souboru msobj90. dll, které mohou být zastaralé.
