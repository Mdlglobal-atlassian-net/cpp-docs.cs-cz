---
title: "Postupy: Přidání podpory správce restartování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a413f28909a52e3bc82e9d8f2694d559bf8a885c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-restart-manager-support"></a>Postupy: Přidání podpory správce restartování
Správce restartování je funkce přidána do [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] pro [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. Správce restartování přidává podporu pro aplikace, pokud se neočekávaně ukončí nebo restartuje. Chování správce restartování závisí na typu aplikace. Pokud je aplikace editor dokumentů, správce restartování povolené automaticky uložit stav aplikace a obsah všechny otevřené dokumenty a restartuje po neočekávaném ukončení aplikace. Pokud vaše aplikace není editor dokumentů, správce restartování restartuje aplikace, ale je ve výchozím nastavení nelze uložit stav aplikace.  
  
 Po restartování aplikace zobrazí dialogové okno úloh, pokud je aplikace kódování Unicode. Pokud je aplikace ANSI, aplikace zobrazí okno se zprávou systému Windows. V tomto okamžiku uživatel rozhodne, zda se mají obnovit automaticky uložené dokumenty. Pokud uživatel není obnovit automaticky uložené dokumenty, správce restartování odstraní dočasné soubory.  
  
> [!NOTE]
>  Můžete přepsat výchozí chování správce restartování pro ukládání dat a restartování aplikace.  
  
 Ve výchozím nastavení, vytvořené pomocí Průvodce projektem v aplikacích MFC [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] podpory správce restartování při spuštění aplikace na počítači, který má [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. Pokud nechcete, aby vaše aplikace pro podporu správce restartování, můžete zakázat správce restartování v Průvodci vytvořením projektu.  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Přidání podpory správce restartování do existující aplikace  
  
1.  Otevřete existující aplikaci MFC v [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
2.  Otevření zdrojového souboru pro hlavní aplikace. Ve výchozím nastavení to je sada soubor, který má stejný název jako vaše aplikace. Zdrojový soubor hlavní aplikace pro MyProject je například MyProject.cpp.  
  
3.  Najít v konstruktoru pro hlavní aplikace. Například pokud je název projektu MyProject, konstruktor je `CMyProjectApp::CMyProjectApp()`.  
  
4.  Přidejte následující řádek kódu do konstruktoru.  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  Zajistěte, aby `InitInstance` metoda aplikace volá nadřazené `InitInstance` metoda: [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) nebo `CWinAppEx::InitInstance`. `InitInstance` Metoda je odpovědná za kontrolu `m_dwRestartManagerSupportFlags` parametr.  
  
6.  Zkompilování a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [CDataRecoveryHandler – třída](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [CWinApp – třída](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

