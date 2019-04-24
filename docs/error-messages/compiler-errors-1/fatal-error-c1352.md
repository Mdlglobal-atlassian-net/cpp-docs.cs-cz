---
title: Závažná chyba C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329722"
---
# <a name="fatal-error-c1352"></a>Závažná chyba C1352

Neplatný nebo poškozený kód MSIL ve funkci 'function' z modulu 'file'

.Netmodule byl předán kompilátoru, ale kompilátor zjistil poškození v souboru.  Požádejte uživatele, který vytváří modul .NET k prozkoumání.

Kompilátor nekontroluje souborů .netmodule pro všechny typy poškození.  , Ale zkontrolujte, že všechny cesty ovládacích prvků ve funkci obsahuje příkaz return.

Další informace najdete v tématu [soubory .netmodule jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).