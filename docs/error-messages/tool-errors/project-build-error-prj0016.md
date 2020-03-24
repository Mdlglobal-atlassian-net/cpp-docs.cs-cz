---
title: Chyba sestavení projektu PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 0cab1e35a36ab78426923d60acafb5cdf2942469
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192741"
---
# <a name="project-build-error-prj0016"></a>Chyba sestavení projektu PRJ0016

Nastavení zabezpečení uživatele brání procesu v jeho vytvoření. Tato nastavení se vyžadují pro sestavování.

Jste přihlášeni jako uživatel, který nemá oprávnění k vytváření procesů pomocí procesu. Musíte změnit úrovně oprávnění pro tento uživatelský účet, nebo se obraťte na správce účtu.

K této chybě může dojít také v případě, že je nastaven následující klíč registru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Tuto chybu můžete vyřešit tak, že odstraníte klíč RestrictRun. Pokud je tento klíč registru potřeba, přidejte **VCSpawn. exe** do seznamu položek v klíči.

Další příčinou této chyby je, že nastavení zásad nezahrnuje VCSpawn. exe do klíče registru HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako povolený program pro tento uživatelský účet.

Další informace najdete v tématu [dodržování nastavení systémových zásad](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings)v části "spouštění pouze povolených aplikací systému Windows".
