---
title: "Přidání ovládacího prvku (ATL – tutoriál, část 2) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aed69a5dd421e967e1da33bb3a2f2c41fa80698d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Přidání ovládacího prvku (ATL – tutoriál, část 2)
V tomto kroku bude přidání ovládacího prvku do projektu, sestavte jej a otestovat ji na webové stránce.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-add-an-object-to-an-atl-project"></a>Chcete-li přidat objekt do projektu knihovny ATL  
  
1.  V zobrazení tříd klikněte pravým tlačítkem na projekt mnohoúhelníku.  
  
2.  Přejděte na příkaz **přidat** na místní nabídky a klikněte na **třída** v podnabídce.  
  
     **Přidat třídu** zobrazí se dialogové okno. Kategorie jiný objekt, jsou uvedeny ve stromové struktuře na levé straně.  
  
3.  Klikněte **ATL** složky.  
  
4.  V seznamu šablon na pravé straně vyberte **ovládací prvek ATL**. Klikněte na tlačítko **přidat**. Otevře se Průvodce ovládacím prvkem ATL a můžete nakonfigurovat řízení.  
  
5.  Typ `PolyCtl` jako krátký název a Všimněte si, že ostatní pole se vyplní automaticky. Neklikejte na **Dokončit** ještě nebyla, protože je nutné provést některé změny.  
  
 Průvodce ovládacím prvkem ATL **názvy** stránka obsahuje následující pole:  
  
|Pole|Obsah|  
|-----------|--------------|  
|**Krátký název**|Název, který jste zadali pro ovládací prvek.|  
|**– Třída**|Název třídy C++ vytvořit k implementaci ovládacího prvku.|  
|**soubor h**|Soubor vytvořený tak, aby obsahovala definice třídy C++.|  
|**souboru**|Soubor vytvořený tak, aby obsahovala implementaci třídy C++.|  
|**Třída typu coClass**|Název třídy součástí pro tento ovládací prvek.|  
|**Rozhraní**|Název rozhraní, na kterém se ovládací prvek implementovat vlastní metody a vlastnosti.|  
|**Typ**|Popis pro ovládací prvek.|  
|**ProgID**|Čitelný název, který lze použít k vyhledání CLSID ovládacího prvku.|  
  
 Je nutné provést několik dalších nastavení v Průvodci ATL ovládacího prvku.  
  
#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Chcete-li povolit podporu pro bohatou chyba informace a spojovacích bodů  
  
1.  Klikněte na tlačítko **možnosti** otevřete **možnosti** stránky.  
  
2.  Vyberte **spojovací body** zaškrtávací políčko. Podpora pro odchozí rozhraní tím se vytvoří v souboru IDL.  
  
 Můžete také nastavit řízení Vložitelný, což znamená, že lze jej vkládat do aplikace, které podporují vložené objekty, jako je například aplikace Excel nebo Word.  
  
#### <a name="to-make-the-control-insertable"></a>Chcete-li Vložitelný ovládacího prvku  
  
1.  Klikněte na tlačítko **vzhled** otevřete **vzhled** stránky.  
  
2.  Vyberte **Insertable** zaškrtávací políčko.  
  
 Zobrazí objekt mnohoúhelníku bude mít barvu výplně plnou, takže budete muset přidat `Fill Color` stock vlastnost.  
  
#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>K přidání uložených vlastností Barva výplně a vytvoření ovládacího prvku  
  
1.  Klikněte na tlačítko **uložené vlastnosti** otevřete **uložené vlastnosti** stránky.  
  
2.  V části **nepodporuje**, projděte dolů seznam možných uložených vlastností. Klikněte dvakrát na `Fill Color` ho chcete přesunout **podporované** seznamu.  
  
3.  Dokončení nastavení pro ovládací prvek. Klikněte na tlačítko **Dokončit**.  
  
 Průvodce vytváření ovládacího prvku, několik změn kódu a přidání souboru došlo k chybě. Byly vytvořeny následující soubory:  
  
|Soubor|Popis|  
|----------|-----------------|  
|PolyCtl.h|Obsahuje většinu implementaci třídy C++ `CPolyCtl`.|  
|PolyCtl.cpp|Obsahuje zbývající části `CPolyCtl`.|  
|PolyCtl.rgs|Textový soubor, který obsahuje skript registru použitá pro zaregistrování ovládacího prvku.|  
|PolyCtl.htm|Obsahující odkaz na nově vytvořený ovládacího prvku na webové stránce.|  
  
 Průvodce také provést následující změny kódu:  
  
-   Přidat `#include` příkaz k souborům stdafx.h a stdafx.cpp zahrnout knihovny ATL soubory potřebné pro podporu ovládací prvky.  
  
-   Změněné Polygon.idl zahrnout podrobnosti nového ovládacího prvku.  
  
-   Přidat nový ovládací prvek pro mapování objektu v Polygon.cpp.  
  
 Nyní můžete vytvořit řízení zobrazíte v akci.  
  
## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku  
  
#### <a name="to-build-and-test-the-control"></a>Pro sestavení a otestování ovládacího prvku  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavení mnohoúhelníku**.  
  
     Po dokončení ovládacího prvku sestavení, klikněte pravým tlačítkem na PolyCtl.htm v **Průzkumníku řešení** a vyberte **zobrazit v prohlížeči**. Zobrazí se obsahující ovládacího prvku HTML webové stránky. Měli byste vidět stránky s názvem "ATL 8.0 zkušební stránku pro objekt PolyCtl" a text **PolyCtl**. Toto je vlastního ovládacího prvku.  
  
> [!NOTE]
>  Po dokončení tohoto kurzu, pokud se zobrazí chybové hlášení, kde nelze vytvořit soubor knihovny DLL, zavřete soubor PolyCtl.htm a kontejner testů ovládací prvek ActiveX a znovu sestavte řešení. Pokud stále nelze vytvořit knihovnu DLL, restartujte počítač nebo odhlášení (Pokud používáte Terminálové služby).  
  
 V dalším kroku přidáte vlastní vlastnosti do ovládacího prvku.  
  
 [Zpátky ke kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [Na krok 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

