---
title: "Vložení ovládacího prvku na webovou stránku (ATL – tutoriál, část 7) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6990539ca6f0bc2956822547e3d41c00c841caf8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Vložení ovládacího prvku na webovou stránku (ATL – tutoriál, část 7)
Vlastní ovládací prvek je nyní dokončena. Vlastní ovládací prvek fungovat v situaci, skutečné najdete ji umístěte na webové stránce. Soubor HTML, který obsahuje ovládací prvek byl vytvořen při definování vlastního ovládacího prvku. Otevřete soubor PolyCtl.htm z **Průzkumníku**, a zobrazí se vaše ovládacího prvku na webové stránce.  
  
 V tomto kroku se skript webové stránky na reakce na události. Pokud upravíte ovládacího prvku do aplikace Internet Explorer vědět, že je ovládací prvek bezpečné pro skriptování.  
  
## <a name="scripting-the-web-page"></a>Skriptování webové stránky  
 Ovládací prvek udělat nic ještě není, takže změna webové stránky na reakce na události, které odešlete.  
  
#### <a name="to-script-the-web-page"></a>Do skriptu webové stránky  
  
1.  Otevřete PolyCtl.htm a vyberte zobrazení HTML. Přidejte následující řádky do kódu HTML. Přidaly po `</OBJECT>` ale předtím, než `</BODY>`.  
  
 ```  
 
 <SCRIPT LANGUAGE="VBScript">  
 <!--  
    Sub PolyCtl_ClickIn(x, y)  
    PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
    PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
 -->  
 </SCRIPT>  
 ```  
  
2.  Uložte soubor HTM.  
  
 Přidali jste některé kód v jazyce VBScript, který získá vlastnost stranách z ovládacího prvku a zvyšuje počet stran o jednu, pokud kliknete na tlačítko uvnitř ovládacího prvku. Pokud kliknete na tlačítko mimo ovládací prvek, se snižuje počet stran o jednu.  
  
## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Označující, že je bezpečné pro skriptování ovládacího prvku  
 Můžete zobrazit webovou stránku pomocí ovládacího prvku v aplikaci Internet Explorer nebo více pohodlně, použijte zobrazení webového prohlížeče, které jsou součástí Visual C++. Informace o vaší ovládacího prvku ve webovém prohlížeči, klikněte pravým tlačítkem na PolyCtl.htm a klikněte na **zobrazit v prohlížeči**.  
  
 Podle aktuální nastavení zabezpečení aplikace Internet Explorer, může se zobrazit zabezpečení výstraha oznamující pole dialogové okno ovládacího prvku nemusí být bezpečný do skriptu a potenciálně může dojít k poškození. Například pokud jste měli ovládacího prvku, který zobrazí soubor, ale také měl `Delete` metoda, která odstranit soubor, je bezpečné pokud ho jenom zobrazit na stránce. Nejsou bezpečné pro skript, ale protože někdo může zavolat `Delete` metoda.  
  
> [!IMPORTANT]
>  V tomto kurzu můžete změnit nastavení zabezpečení v Internet Exploreru spuštění ovládacích prvků ActiveX, které nejsou označeny jako bezpečné. V Ovládacích panelech klikněte na tlačítko **vlastnosti Internetu** a klikněte na tlačítko **zabezpečení** změnit příslušná nastavení. Pokud jste dokončili kurz, změňte nastavení zabezpečení zpět do původního stavu.  
  
 Internet Explorer můžete výstrahu prostřednictvím kódu programu nemusí zobrazit dialogové okno upozornění zabezpečení pro tento konkrétní ovládací prvek. Můžete to provést pomocí `IObjectSafety` rozhraní a knihovny ATL poskytuje implementace tohoto rozhraní ve třídě [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Chcete-li přidat rozhraní do vlastního ovládacího prvku, přidejte `IObjectSafetyImpl` do seznamu zděděné třídy a přidejte položku pro něj na mapě COM.  
  
#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Chcete-li přidat IObjectSafetyImpl do ovládacího prvku  
  
1.  Přidejte následující řádek na konec seznamu zděděné třídy v PolyCtl.h a přidejte čárka na předchozí řádek:  
  
 [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  Přidejte následující řádek na mapu modelu COM v PolyCtl.h:  
  
 [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku  
 Vytvoření ovládacího prvku. Po dokončení sestavení, otevřete znovu PolyCtl.htm v zobrazit v prohlížeči. Tentokrát přímo bez dialogové okno výstrahy zabezpečení by měl zobrazí webová stránka. Klikněte na tlačítko uvnitř mnohoúhelníku; počet stran se zvýší o 1. Klikněte na mimo mnohoúhelníku a snížit počet stranách. Pokud se pokusíte snížit počet stran pod tři, zobrazí se chybová zpráva, která nastavíte.  
  
 [Zpět na krok 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="next-steps"></a>Další kroky  
 Tím je kurz ATL ukončen. Odkazy na další informace o rozhraní ATL, najdete v článku [ATL úvodní stránku](../atl/active-template-library-atl-concepts.md).  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

