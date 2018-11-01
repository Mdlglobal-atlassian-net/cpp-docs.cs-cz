---
title: Předkompilované soubory hlaviček
ms.date: 11/04/2016
f1_keywords:
- stdafx.h
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
ms.openlocfilehash: fed583464aa172887b80a8551adf86e02a76d210
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643206"
---
# <a name="precompiled-header-files"></a>Předkompilované soubory hlaviček

Tyto soubory se používají k sestavení předkompilovaného hlavičkového souboru *název_projektu*.pch a předkompilované typy soubor Stdafx.obj.

Tyto soubory jsou umístěny v *název_projektu* adresáře. V Průzkumníku řešení Stdafx.h je ve složce hlavičkové soubory a Stdafx.cpp se nachází ve složce zdrojové soubory.

|Název souboru|Popis|
|---------------|-----------------|
|Stdafx.h|Zahrnout soubor pro standardní systémové soubory zahrnutí a specifické pro projekt zahrnuté soubory, které jsou často používány, ale se mění jen zřídka.<br /><br /> By neměl definovat nebo některý z _AFX_NO_XXX v souboru stdafx.h nedefinované.|
|Stdafx.cpp|Obsahuje direktivy preprocesoru `#include "stdafx.h"` a přidá zahrnout soubory pro předkompilované typy. Předkompilované soubory libovolného typu, včetně souborů záhlaví, podporují kratší časy kompilace omezením kompilace pouze na tyto soubory, které je vyžadují. Jakmile se váš projekt se vytvořil poprvé, můžete si všimnout, sestavení mnohem rychlejší u následujících sestavení z důvodu přítomnosti předkompilované hlavičkové soubory.|

## <a name="see-also"></a>Viz také

[Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)