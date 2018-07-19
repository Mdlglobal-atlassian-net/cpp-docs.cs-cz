---
title: Vytvoření projektu (ATL – tutoriál, část 1) | Dokumentace Microsoftu
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1906ac1ae8c1e526d78690e131a7ca5147283d76
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025923"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Vytvoření projektu (ATL – tutoriál, část 1)
Tento kurz vás provede bez atributové projekt knihovny ATL, který vytvoří objekt ActiveX, který zobrazí mnohoúhelníku. Objekt obsahuje možnosti pro povolení uživatele Chcete-li změnit počet stran tvořící mnohoúhelníků a kódu, aktualizujte zobrazení.  
  
> [!NOTE]
>  ATL a MFC nejsou podporovány obecně v edicích Express sady Visual Studio.  
  
> [!NOTE]
>  Tento kurz vytvoří stejný zdrojový kód jako ukázka mnohoúhelníku. Pokud chcete se vyhnout ručním zadáním zdrojového kódu, můžete ji stáhnout [abstraktní ukázky mnohoúhelníku](../visual-cpp-samples.md). Poté můžete odkázat ke zdrojovému kódu mnohoúhelníku při projít tento kurz, a použít ho ke kontrole chyb ve vašem vlastním projektu.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Chcete-li vytvořit počáteční projekt knihovny ATL pomocí Průvodce projektem ATL  
  
1.  Ve vývojovém prostředí sady Visual Studio, klikněte na tlačítko **nový** na **souboru** nabídky a pak klikněte na tlačítko **projektu**.  
  
2.  Klikněte na tlačítko **projekty Visual C++** a pak zvolte položku **projekt knihovny ATL**.  
  
3.  Typ *mnohoúhelníku* jako název projektu.  
  
     Umístění pro zdrojový kód se obvykle ve výchozím nastavení projekty Documents\Visual Studio a automaticky se vytvoří novou složku.  
  
4.  Klikněte na tlačítko **OK** a otevře se Průvodce projektem ATL.  
  
5.  Klikněte na tlačítko **nastavení aplikace** chcete zobrazit dostupné možnosti.  
  
6.  Jako jsou vytvoření ovládacího prvku a ovládací prvek musí být v procesový server, ponechte **typ aplikace** jako knihovnu DLL.  
  
7.  U ostatních možností ponechte jejich výchozí hodnoty a klikněte na tlačítko **Dokončit**.  
  
 Průvodce projektem ATL vytvoří vygenerováním několik souborů projektu. Tyto soubory můžete zobrazit v Průzkumníku řešení tak, že rozbalíte objekt mnohoúhelníku. Soubory jsou uvedeny níže.  
  
    |Soubor|Popis|  
    |----------|-----------------|  
    |Polygon.cpp|Obsahuje implementaci `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, a `DllUnregisterServer`. Obsahuje také mapy objektu, která je seznamu objektů knihovny ATL v projektu. Toto je původně prázdné.|  
    |Polygon.def|Tento soubor definice modulu poskytuje linkeru s informacemi o exportech vyžadované vaší knihovny DLL.|  
    |Polygon.IDL|Rozhraní language souboru definice, které popisuje specifické pro objekty rozhraní.|  
    |Polygon.rgs|Tento skript registru obsahuje informace o registraci knihovny DLL váš program.|  
    |Polygon.rc|Soubor prostředků, která původně obsahuje informace o verzi a řetězec obsahující název projektu.|  
    |Resource.h|Hlavičkový soubor pro soubor prostředků.|  
    |Polygonps.def|Tento soubor definice modulu poskytuje linkeru s informacemi o vývozu vyžadované kódu proxy a zástupných procedur, které podporují volání napříč objekty apartment.|  
    |stdafx.cpp|Soubor, který bude `#include` ATL implementační soubory.|  
    |stdafx.h|Soubor, který bude `#include` hlavičkové soubory ATL.|  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem myši `Polygon` projektu.  
  
2.  V místní nabídce klikněte na tlačítko **vlastnosti**.  
  
3.  Klikněte na **Linkeru**. Změnit **za UserRedirection** umožňuje **Ano**.  
  
4.  Klikněte na tlačítko **OK**.  
  
 V dalším kroku přidáte ovládací prvek do projektu.  
  
 [Ke kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

