---
title: Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8e5065cebab002e9c48aef560eb9f2feab67e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33321623"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček
Následující soubory se vytvoří při vytváření projektu knihovny ATL v sadě Visual Studio, v závislosti na možnosti, kterou jste vybrali pro projekt, který vytvoříte.  
  
 Všechny tyto soubory jsou umístěny v *Projname* adresář a v složky (hlaviček soubory) nebo zdrojové soubory (soubory sada) složky v Průzkumníku řešení.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|*Projname*.h|Hlavní soubor obsahující definice rozhraní C++ a deklarace identifikátoru GUID položky definované v ATLSample.idl. Jsou obnoveny pomocí MIDL během kompilace.|  
|*Projname*sada|Zdrojový soubor hlavní aplikace. Obsahuje implementace exportu knihovny DLL v procesu serveru a provádění `WinMain` pro místní server. Pro službu dále implementuje všechny funkce správy služeb.|  
|Resource.h|Hlavičky souboru pro soubor prostředků.|  
|StdAfx.cpp|Zahrnuje soubory StdAfx.h a Atlimpl.cpp.|  
|StdAfx.h|Zahrnuje knihovny ATL hlavičkových souborů.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](../ide/mfc-program-or-control-source-and-header-files.md)   
 [CLR – projekty](../ide/files-created-for-clr-projects.md)