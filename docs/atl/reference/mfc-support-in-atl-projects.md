---
title: Podpora MFC v projekty knihovny ATL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.atl.addmfc
dev_langs: C++
helpviewer_keywords: ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0217c62ff207ad706dbcb1cd172e878c2b96daee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-support-in-atl-projects"></a>Podpora MFC v projekty knihovny ATL
Pokud vyberete **Podpora MFC** v Průvodci projektu knihovny ATL deklaruje projekt aplikace jako objekt aplikace knihovny MFC (třída). Projekt inicializuje knihovny MFC a vytvoří instanci třídy (třídy *ProjName*) je odvozena z [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Tato možnost je k dispozici pro pouze neoznačené atributy projekty knihovny ATL DLL.  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
 
// Overrides  
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP() 
};  
 
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
 
CProjNameApp theApp;  
 
BOOL CProjNameApp::InitInstance()  
{  
    return CWinApp::InitInstance();

}  
 
int CProjNameApp::ExitInstance()  
{  
    return CWinApp::ExitInstance();

}  
```  
  
 Můžete zobrazit třídu objektu aplikace a její `InitInstance` a `ExitInstance` funkcí v zobrazení tříd.  
  
## <a name="see-also"></a>Viz také  
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Vytvoření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)   
 [Výchozí konfigurace projektu knihovny ATL](../../atl/reference/default-atl-project-configurations.md)

