---
title: "Chyba sestavení projektu PRJ0016 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0016
dev_langs: C++
helpviewer_keywords: PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9aa96ec353dbe236744a6a9baa5ad18ff25451d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0016"></a>Chyba sestavení projektu PRJ0016
Nastavení zabezpečení uživatele zabránit procesu vytváření. Tato nastavení se vyžadují pro vytvoření.  
  
 Jste přihlášeni jako uživatel, který nemá oprávnění k vytvoření procesů pomocí procesu. Musíte změnit úrovně oprávnění pro tento uživatelský účet, nebo požádejte správce účtu.  
  
 Tato chyba může vyskytnout, pokud je nastaven následující klíč registru:  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 Pokud chcete tuto chybu vyřešit, odstraňte klíč RestrictRun. V případě potřeby tento klíč registru připojit **vcspawn.exe** do seznamu položek v klíči.  
  
 Další příčinou této chyby je, že vaše zásady nastavení nezahrnuje VCSpawn.exe v klíči registru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako Povolené okno program pro tento uživatelský účet.  
  
 Další informace najdete v tématu:  
  
-   Článek znalostní báze Knowledge Base 324153, která je k dispozici na [http://support.microsoft.com/default.aspx?scid=kb;en-us;324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).  
  
-   [Dodržujte zásady nastavení systému](http://msdn.microsoft.com/library/aa372139), v sekci "Spouštět pouze povolené aplikace systému Windows".