---
title: Podpora MFC v projektech ATL
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 0aece6805f1de987b0164f405e50b99fd706fef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275422"
---
# <a name="mfc-support-in-atl-projects"></a>Podpora MFC v projektech ATL

Pokud vyberete **podpora knihovny MFC** Průvodce projektem ATL do projektu deklaruje aplikace jako objekt aplikace knihovny MFC (třídy). Projekt knihovny MFC inicializuje a vytvoří instanci třídy (třídy *název_projektu*), která je odvozena od [CWinApp](../../mfc/reference/cwinapp-class.md).

Tato možnost je dostupná bez atributové ATL DLL pouze pro projekty.

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

Můžete zobrazit třídu objektu aplikace a její `InitInstance` a `ExitInstance` funkce v zobrazení tříd.

## <a name="see-also"></a>Viz také:

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)
