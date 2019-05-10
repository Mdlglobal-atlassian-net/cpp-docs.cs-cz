---
title: Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 15d49cf984e45feeaad454de13c4ab37622000a4
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446577"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Program knihovny ATL nebo zdroj ovládacího prvku a soubory hlaviček

Následující soubory jsou vytvořeny při vytvoření projektu knihovny ATL v sadě Visual Studio, v závislosti na možnostech, které vyberete pro projekt, který vytvoříte.

Všechny tyto soubory jsou umístěny v *název_projektu* adresář a soubory hlaviček (.h souborů), složku nebo zdrojové soubory (.cpp) složku v Průzkumníku řešení.

|Název souboru|Popis|
|---------------|-----------------|
|*Název_projektu*.h|Hlavní zahrnout soubor obsahující definice rozhraní C++ a deklarace identifikátoru GUID položky definované v ATLSample.idl. MIDL – to je regenerována během kompilace.|
|*Projname*.cpp|Zdrojový soubor hlavního programu. Obsahuje implementace exportu knihovny DLL v procesu serveru a provádění `WinMain` pro místní server. Pro službu dále implementuje všechny funkce správy služeb.|
|Resource.h|Hlavičkový soubor pro soubor prostředků.|
|StdAfx.cpp|Zahrnuje souborů StdAfx.h a Atlimpl.cpp.|
|StdAfx.h|Obsahuje hlavičkové soubory ATL.|

## <a name="see-also"></a>Viz také:

[Soubor typy vytvořené pro vizuál C++ projekty](file-types-created-for-visual-cpp-projects.md)<br>
[Program knihovny MFC nebo zdroj ovládacího prvku a soubory hlaviček](mfc-program-or-control-source-and-header-files.md)<br>
[Projekty CLR](files-created-for-clr-projects.md)
