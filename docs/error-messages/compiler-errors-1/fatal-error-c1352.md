---
title: Závažná chyba C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648679"
---
# <a name="fatal-error-c1352"></a>Závažná chyba C1352

Neplatný nebo poškozený kód MSIL ve funkci 'function' z modulu 'file'

.Netmodule byl předán kompilátoru, ale kompilátor zjistil poškození v souboru.  Požádejte uživatele, který vytváří modul .NET k prozkoumání.

Kompilátor nekontroluje souborů .netmodule pro všechny typy poškození.  , Ale zkontrolujte, že všechny cesty ovládacích prvků ve funkci obsahuje příkaz return.

Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).