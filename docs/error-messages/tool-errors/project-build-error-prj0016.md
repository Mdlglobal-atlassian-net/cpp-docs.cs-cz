---
title: Chyba sestavení projektu PRJ0016 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01610f888d8afe275b0e52b86e4f4c678f896c9f
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820466"
---
# <a name="project-build-error-prj0016"></a>Chyba sestavení projektu PRJ0016

Nastavení zabezpečení uživatele zabránit procesu vytváření. Tato nastavení pro sestavování jsou vyžadována.

Jste přihlášeni jako uživatel, který nemá oprávnění k vytváření procesů pomocí procesu. Musíte změnit úrovně oprávnění pro tento uživatelský účet nebo kontaktujte správce účtu.

K této chybě může dojít, pokud nastavte následující klíč registru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Chcete-li tuto chybu vyřešit, odstraňte klíč RestrictRun. Pokud tento klíč registru je potřeba, připojte **vcspawn.exe** do seznamu položek v klíči.

Další příčinou této chyby je, že vaše nastavení zásad nezahrnuje VCSpawn.exe v klíči registru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako Povolené program okno pro tento uživatelský účet.

Další informace najdete v tématu:

- Znalostní báze Knowledge Base 324153, která je k dispozici na [ http://support.microsoft.com/default.aspx?scid=kb; 324153](http://support.microsoft.com/default.aspx?scid=kb;324153).

- [Týkajícími se nastavení zásad systému](https://msdn.microsoft.com/library/aa372139), v sekci "Spouštět pouze povolené aplikace Windows".