---
title: Dynamické rozložení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7518e2fdd07254b8b1991fae8a41f26058920858
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350846"
---
# <a name="dynamic-layout"></a>Dynamické rozložení
MFC ve Visual Studiu 2015 dialogová okna, které uživatel může změnit velikost můžete vytvořit a můžete řídit způsob, jakým upraví rozložení pro změnu velikosti. Tlačítka v dolní části dialogového okna můžete například připojit k dolnímu okraji tak, aby zůstaly vždy v dolní části. Můžete také nastavit určité ovládací prvky, jako je například textová pole, rozevírací seznamy a editboxes rozbalte jako uživatel rozšíří dialogové okno.  
  
## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Zadání nastavení dynamické rozložení pro dialogového okna knihovny MFC  
 Když uživatel změní velikost dialogové okno, ovládací prvky v dialogovém okně můžete změnit velikost nebo v směrech X a Y. Dynamické rozložení se označuje změnu v hodnotě velikosti nebo umístění ovládacího prvku, když uživatel změní velikost dialogové okno. Například následující je dialogové okno před změnu velikosti:  
  
 ![Dialogové okno před změnu velikosti. ] (../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")  
  
 Po změnou velikosti, oblasti listbox je zvýšena na Zobrazit více položek a tlačítka se přesouvají společně s pravém dolním rohu:  
  
 ![Dialogové okno po změnu velikosti. ] (../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")  
  
 Dynamické rozložení můžete řídit zadáním podrobnosti pro každý ovládací prvek v editoru prostředků v prostředí IDE, nebo to můžete provést sestavují programově pomocí přístupu k objektu CMFCDynamicLayout pro konkrétní ovládací prvek a nastavení vlastností.  
  
### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Dynamické rozložení vlastnosti nastavení v editoru prostředků  
 Dynamické rozložení chování pro dialogové okno můžete nastavit bez nutnosti psaní jakéhokoli kódu pomocí editoru prostředků.  
  
##### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Chcete-li nastavit vlastnosti dynamické rozložení v editoru prostředků  
  
1.  Pomocí projektu MFC otevřený otevřete dialogové okno, které chcete pracovat v editoru dialogového okna.  
  
     ![Otevřete dialogové okno v editoru prostředků. ] (../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")  
  
2.  Vyberte ovládací prvek a v okně vlastností nastavte její vlastnosti dynamické rozložení. **Dynamické rozložení** oddíl v okně Vlastnosti obsahuje vlastnosti **přesun typ**, **typ nastavení velikosti**a v závislosti na vybrané pro tyto vlastnosti hodnoty konkrétní vlastnosti, které definují kolik ovládací prvky přesunout nebo změňte velikost. **Přesunutí typ** Určuje, jak přesunout ovládacího prvku jako se změní velikost dialogového okna; **Typ nastavení velikosti** Určuje, jak je nastavena velikost ovládacího prvku jako se změní velikost dialogového okna. **Přesunutí typ** a **typ nastavení velikosti** může být **vodorovné**, **svislé**, **i**, nebo **žádné**v závislosti na dimenzí, které chcete změnit dynamicky. Vodorovný je dimenze X; Svislý je směru osy Y.  
  
3.  Pokud chcete ovládací prvek tlačítko na pevnou velikost a umístění v pravé dolní zůstane, jako je běžné, že **OK** nebo **zrušit** tlačítka, nastavte **typ nastavení velikosti** k  **Žádné**a nastavte **přesun typ** k **i**. Pro **přesun X** a **přesun Y** hodnoty v části **přesun typ**, nastavte 100 % pro ovládací prvek, aby zůstat pevné vzdálenost od dolní pravém rohu.  
  
     ![Dynamické rozložení](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")  
  
4.  Předpokládejme, že máte také ovládací prvek, který chcete rozšířit jako rozšíří dialogové okno. Obvykle uživatel může rozšířit dialogové okno Chcete-li rozbalit Víceřádkový textové pole pro zvětšení velikosti oblasti textového nebo se může rozšířit ovládací prvek seznamu zobrazíte další data. Pro tento případ, nastavte **typ nastavení velikosti** do obou a nastavte **přesun typ** na hodnotu none. Potom nastavte **nastavení velikosti X** a **nastavení velikosti Y** hodnoty do 100.  
  
     ![Dynamické rozložení nastavení](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")  
  
5.  Experimentujte s jiné hodnoty, které může mít smysl pro vaše ovládací prvky. Dialogové okno s jednořádkové textové pole můžou mít **typ nastavení velikosti** nastavena na **vodorovné** pouze, například.  
  
### <a name="setting-dynamic-layout-properties-programmatically"></a>Nastavení vlastností dynamické rozložení prostřednictvím kódu programu  
 Předchozí postup je užitečný pro zadání vlastnosti dynamické rozložení pro dialogové okno v době návrhu, ale pokud chcete řídit dynamické rozložení za běhu, můžete nastavit vlastnosti dynamické rozložení prostřednictvím kódu programu.  
  
##### <a name="to-set-dynamic-layout-properties-programmatically"></a>Chcete-li nastavit vlastnosti dynamické rozložení prostřednictvím kódu programu  
  
1.  Najít nebo vytvořit místo v kódu implementace třídy dialogového okna, ve které chcete zadat dynamické rozložení pro dialogové okno. Například můžete chtít například přidání metody `AdjustLayout` v dialogovém okně a volání z umístí kde je potřeba změnit rozložení. Může nejprve zavolat to z konstruktoru, nebo po provedení změn do dialogového okna.  
  
2.  Pro dialogové okno, volání [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), metoda třídy CWnd. GetDynamicLayout vrátí ukazatel na objekt CMFCDynamicLayout.  
  
 ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();

 ```  
  
3.  Pro první prvek, ke které chcete přidat dynamické chování, použít statické metody pro třídu dynamické rozložení pro vytvoření [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) struktura, která kóduje způsob, jakým je třeba upravit ovládacího prvku. To uděláte tak, že první zvolíte odpovídající statickou metodu: [CMFCDynamicLayout::MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout::MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout::MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone), nebo [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Předáte vodorovné nebo svislé aspektů přesunutí v procentech. Tato statické metody všechny vrátí nově vytvořený objekt MoveSettings, který můžete použít k určení chování přesunutí ovládacího prvku.  
  
     Mějte na paměti, že 100 znamená přesunout přesně tolik, kolik dialogové okno změní velikost, což způsobí, že okraj ovládacího prvku zůstane pevné vzdálenost od nové ohraničení.  
  
 ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);

 ```  
  
4.  Chování velikost, která používá stejnou věc udělat [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) typu. Například zadejte ovládacího prvku při dialogové okno změní nemění velikost, použijte následující kód:  
  
 ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();

 ```  
  
5.  Přidání ovládacího prvku do správce dynamické rozložení pomocí [CMFCDynamicLayout::AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) metoda. Existují dvě přetížení pro různé způsoby zadávání požadovaný ovládací prvek. Má popisovač okna ovládacího prvku (HWND) a dalších trvá ID ovládacího prvku.  
  
 ```  
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);

 ```  
  
6.  Opakujte pro každý ovládací prvek, který chcete přesunout nebo změně velikosti.  
  
7.  Pokud potřebujete, můžete použít [CMFCDynamicLayout::HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) metoda k určení, pokud ovládací prvek již je na seznamu ovládacích prvků podrobí dyamic rozložení změny, nebo [CMFCDynamicLayout::IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) Metoda, která určí, jestli jsou všechny ovládací prvky, které se vztahují změny.  
  
8.  Chcete-li povolit rozložení dialogové okno, zavolejte [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) metoda.  
  
 ```  
    pDialog->EnableDynamicLayout(TRUE);

 ```  
  
9. Při příštím uživatel změní velikost dialogového okna, [CMFCDynamicLayout::Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) metoda je volána, která ve skutečnosti aplikuje nastavení.  
  
10. Pokud chcete zakázat dynamické rozložení, zavolejte [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) s `FALSE` jako u `bEnabled` parametr.  
  
 ```  
    pDialog->EnableDynamicLayout(FALSE);

 ```  
  
##### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Chcete-li nastavit dynamické rozložení prostřednictvím kódu programu ze zdrojového souboru  
  
1.  Použití [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) metodu zadejte název prostředku v souboru skriptu relevantní prostředků (.rc soubor), který určuje dynamické rozložení informace, jako v následujícím příkladu:  
  
 ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");

 ```  
  
     S názvem prostředku, musí odkazovat dialog, který obsahuje informace o rozvržení ve formě AFX_DIALOG_LAYOUT položku v souboru prostředků, jako v následujícím příkladu:  
  
 ''' * / / / * / / * / NEBO AFX_DIALOG_LAYOUT * / /  
 
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    ZAČNĚTE 0X0000, 0X6400, 0X0028, 0X643C, 0X0028  
    END 
 
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    ZAČNĚTE 0X0000, 0X6464, 0X0000, 0X6464, 0X0000, 0X0000, 0X6464, 0X0000, 0X0000  
 
    END 
 ```  
  
## See Also  
 [CMFCDynamicLayout Class](../mfc/reference/cmfcdynamiclayout-class.md)   
 [Control Classes](../mfc/control-classes.md)   
 [Dialog Box Classes](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../windows/dialog-editor.md)

