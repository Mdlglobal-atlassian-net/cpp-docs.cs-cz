---
title: Závažná chyba C1352 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4f1f062e11651e4d851231e16569412f95b90d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042933"
---
# <a name="fatal-error-c1352"></a>Závažná chyba C1352

Neplatný nebo poškozený kód MSIL ve funkci 'function' z modulu 'file'

.Netmodule byl předán kompilátoru, ale kompilátor zjistil poškození v souboru.  Požádejte uživatele, který vytváří modul .NET k prozkoumání.

Kompilátor nekontroluje souborů .netmodule pro všechny typy poškození.  , Ale zkontrolujte, že všechny cesty ovládacích prvků ve funkci obsahuje příkaz return.

Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).