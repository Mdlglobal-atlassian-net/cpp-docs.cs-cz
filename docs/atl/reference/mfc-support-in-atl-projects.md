---
title: Podpora MFC v projektech ATL | Dokumentace Microsoftu
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
ms.openlocfilehash: ad9e55fa296b8a39e4c77ab33240c837b6c871ea
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063494"
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

## <a name="see-also"></a>Viz také

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md)

