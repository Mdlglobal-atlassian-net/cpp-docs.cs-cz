---
title: Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček | Dokumentace Microsoftu
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
ms.openlocfilehash: 95fa6fa506e4f471b90d39659b0908e2755b72b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398700"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček

Následující soubory jsou vytvořeny při vytvoření projektu knihovny ATL v sadě Visual Studio, v závislosti na možnostech, které vyberete pro projekt, který vytvoříte.

Všechny tyto soubory jsou umístěny v *název_projektu* adresář a soubory hlaviček (.h souborů), složku nebo zdrojové soubory (.cpp) složku v Průzkumníku řešení.

|Název souboru|Popis|
|---------------|-----------------|
|*Název_projektu*.h|Hlavní zahrnout soubor obsahující definice rozhraní C++ a deklarace identifikátoru GUID položky definované v ATLSample.idl. MIDL – to je regenerována během kompilace.|
|*Název_projektu*.cpp|Zdrojový soubor hlavního programu. Obsahuje implementace exportu knihovny DLL v procesu serveru a provádění `WinMain` pro místní server. Pro službu dále implementuje všechny funkce správy služeb.|
|Resource.h|Hlavičkový soubor pro soubor prostředků.|
|StdAfx.cpp|Zahrnuje souborů StdAfx.h a Atlimpl.cpp.|
|StdAfx.h|Obsahuje hlavičkové soubory ATL.|

## <a name="see-also"></a>Viz také

[Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](../ide/mfc-program-or-control-source-and-header-files.md)<br>
[Projekty CLR](../ide/files-created-for-clr-projects.md)