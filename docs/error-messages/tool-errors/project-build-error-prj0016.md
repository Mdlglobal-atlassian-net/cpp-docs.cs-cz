---
title: Chyba sestavení projektu PRJ0016 | Microsoft Docs
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
ms.openlocfilehash: 6184e5bb251a2b74e8500cc195a38f2d814c1b5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0016"></a>Chyba sestavení projektu PRJ0016
Nastavení zabezpečení uživatele zabránit procesu vytváření. Tato nastavení se vyžadují pro vytvoření.  
  
 Jste přihlášeni jako uživatel, který nemá oprávnění k vytvoření procesů pomocí procesu. Musíte změnit úrovně oprávnění pro tento uživatelský účet, nebo požádejte správce účtu.  
  
 Tato chyba může vyskytnout, pokud je nastaven následující klíč registru:  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 Pokud chcete tuto chybu vyřešit, odstraňte klíč RestrictRun. V případě potřeby tento klíč registru připojit **vcspawn.exe** do seznamu položek v klíči.  
  
 Další příčinou této chyby je, že vaše zásady nastavení nezahrnuje VCSpawn.exe v klíči registru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako Povolené okno program pro tento uživatelský účet.  
  
 Další informace najdete v tématu:  
  
-   Článek znalostní báze Knowledge Base 324153, která je k dispozici na [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).  
  
-   [Dodržujte zásady nastavení systému](http://msdn.microsoft.com/library/aa372139), v sekci "Spouštět pouze povolené aplikace systému Windows".