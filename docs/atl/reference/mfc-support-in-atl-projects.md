---
title: Podpora MFC v projekty knihovny ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d42afec863695b1cab05c2d3cf2f65f3d64a1507
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360638"
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
 [Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

