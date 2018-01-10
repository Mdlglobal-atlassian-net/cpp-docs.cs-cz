---
title: "Vytvoření projektu (ATL – tutoriál, část 1) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a9a5fc9a0d2175a419bbc0fb1aacbc9ea25006c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Vytvoření projektu (ATL – tutoriál, část 1)
V tomto kurzu provede vás provede procesem neoznačené atributy ATL projekt, který vytvoří objekt ActiveX, který zobrazí mnohoúhelníku. Objekt obsahuje možnosti pro povolení uživatele Chcete-li změnit počet stran tvořících mnohoúhelníku a kód aktualizovat zobrazení.  
  
> [!NOTE]
>  ATL a MFC nepodporuje obecně edice Express sady Visual Studio.  
  
> [!NOTE]
>  V tomto kurzu vytvoří ze stejného zdrojového kódu jako ukázka mnohoúhelníku. Pokud chcete, aby se zabránilo ručně zadat zdrojový kód, si můžete stáhnout z [mnohoúhelníku ukázka abstraktní](../visual-cpp-samples.md). Pak najdete ve zdrojovém kódu mnohoúhelníku absolvování tohoto kurzu, nebo použít ke kontrole chyb v vlastní projektu.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Chcete-li vytvořit počáteční projekt knihovny ATL pomocí Průvodce projektu knihovny ATL  
  
1.  Ve vývojovém prostředí sady Visual Studio, klikněte na tlačítko **nový** na **soubor** nabídce a pak klikněte na tlačítko **projektu**.  
  
2.  Klikněte **projekty Visual C++** složky a vyberte **projektu knihovny ATL**.  
  
3.  Typ `Polygon` jako název projektu.  
  
     Moje Documents\Visual Studio projekty obvykle použije výchozí umístění pro zdrojový kód a automaticky se vytvoří novou složku.  
  
4.  Klikněte na tlačítko **OK** a otevře se Průvodce projektu knihovny ATL.  
  
5.  Klikněte na tlačítko **nastavení aplikace** zobrazíte možnosti dostupné.  
  
6.  Jako jsou vytvoření ovládacího prvku a ovládacího prvku musí být proces serveru, ponechejte **typ aplikace** jako knihovny DLL.  
  
7.  Ponechte výchozí hodnoty další možnosti a klikněte na tlačítko **Dokončit**.  
  
 Průvodce projektem ATL vytvoří projekt vygenerováním několik souborů. Tyto soubory můžete zobrazit v Průzkumníku řešení rozšířením objekt mnohoúhelníku. Soubory jsou uvedeny níže.  
  
|Soubor|Popis|  
|----------|-----------------|  
|Polygon.cpp|Obsahuje implementace `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, a `DllUnregisterServer`. Také obsahuje mapování objektu, který je seznamu objektů knihovny ATL v projektu. Toto je původně prázdné.|  
|Polygon.def|Tento soubor definice modulu poskytuje linkeru s informacemi o exporty vyžadují knihovny DLL.|  
|Polygon.IDL|Rozhraní definice souboru jazyka, který popisuje specifické pro vaše objekty rozhraní.|  
|Polygon.rgs|Tento skript registru obsahuje informace o registraci vašeho programu DLL.|  
|Polygon.rc|Soubor prostředků, který původně obsahuje informace o verzi a řetězec obsahující název projektu.|  
|Resource.h|Hlavičky souboru pro soubor prostředků.|  
|Polygonps.def|Tento soubor definice modulu poskytuje linkeru s informacemi o exporty vyžadovanou kód serveru proxy a se zakázaným inzerováním podporující volání napříč Apartment.|  
|stdafx.cpp|Soubor, který bude `#include` ATL implementace soubory.|  
|stdafx.h|Soubor, který bude `#include` ATL hlavičkových souborů.|  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem myši `Polygon` projektu.  
  
2.  V místní nabídce klikněte na tlačítko **vlastnosti**.  
  
3.  Klikněte na **Linkeru**. Změna **za UserRedirection** možnost k **Ano**.  
  
4.  Click **OK**.  
  
 V dalším kroku přidáte ovládacího prvku do projektu.  
  
 [Na krok 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

