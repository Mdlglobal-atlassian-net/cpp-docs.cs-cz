---
title: Dynamické rozložení
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 1b0d035d3c551fd309d515ccb8b22159218c1b0a
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "70907551"
---
# <a name="dynamic-layout"></a>Dynamické rozložení

Pomocí knihovny MFC v aplikaci Visual Studio 2015 můžete vytvořit dialogová okna, jejichž velikost může uživatel měnit, a můžete řídit způsob, jakým se upraví rozložení na změnu velikosti. Například můžete připojit tlačítka v dolní části dialogového okna k dolnímu okraji, aby vždy zůstaly v dolní části. Můžete také nastavit určité ovládací prvky, jako jsou například listboxs, editboxes a textová pole, která se mají rozbalit, když uživatel rozbalí dialogové okno.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Zadání nastavení dynamického rozložení pro dialogové okno knihovny MFC

Když uživatel změní velikost dialogového okna, ovládací prvky v dialogovém okně mohou změnit velikost nebo přesun v směrech X a Y. Změna velikosti nebo pozice ovládacího prvku v případě, že uživatel změní velikost dialogového okna se nazývá dynamické rozložení. Například následuje dialogové okno před změnou velikosti:

![Před změnou velikosti dialogového okna.](../mfc/media/mfcdynamiclayout4.png "Před změnou velikosti dialogového okna.")

Po změně velikosti je oblast seznamu zvětšena tak, aby zobrazovala více položek, a tlačítka budou přesunuta spolu s pravým dolním rohem:

![Po změně velikosti dialogového okna.](../mfc/media/mfcdynamiclayout5.png "Po změně velikosti dialogového okna.")

Můžete řídit dynamické rozložení zadáním podrobností pro každý ovládací prvek v editoru prostředků v integrovaném vývojovém prostředí (IDE), nebo můžete to provést programově pomocí přístupu k objektu `CMFCDynamicLayout` pro konkrétní ovládací prvek a nastavením vlastností.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Nastavení vlastností dynamického rozložení v editoru prostředků

Chování dynamického rozložení dialogového okna můžete nastavit bez nutnosti psát jakýkoli kód pomocí editoru prostředků.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Nastavení vlastností dynamického rozložení v editoru prostředků

1. Otevřete projekt knihovny MFC a otevřete dialogové okno, se kterým chcete pracovat v editoru dialogových oken.

   ![Otevřete dialogové okno v editoru prostředků.](../mfc/media/mfcdynamiclayout3.png "Otevřete dialogové okno v editoru prostředků.")

1. Vyberte ovládací prvek a v okně **vlastnosti** (v **zobrazení tříd**) nastavte jeho vlastnosti dynamického rozložení. Oddíl **dynamické rozložení** v okně **vlastnosti** obsahuje vlastnosti **klouzavého typu**, **typ změny velikosti**a v závislosti na hodnotách vybraných pro tyto vlastnosti, specifické vlastnosti, které definují, kolik ovládacích prvků se přesouvá nebo změnit velikost. **Typ přesunutí** určuje způsob přesunutí ovládacího prvku při změně velikosti dialogového okna. **Typ změny** velikosti určuje, jak se změní velikost ovládacího prvku při změně velikosti dialogového okna. **Posunutí typu** a **typ velikosti** může být **vodorovné**, **svislé**, **obojí**nebo **žádné** v závislosti na rozměrech, které chcete dynamicky měnit. Horizontální je rozměr X; Svislá je směr Y.

1. Pokud chcete, aby ovládací prvek jako tlačítko měl být v pevné velikosti a zůstal na místě vpravo dole, jako je to pro tlačítka **OK** nebo **Storno** , nastavte **typ velikosti** na **žádná**a jako **typ přesunu** nastavte **oba**. Pro **přesunutí hodnot X** a **posunutí hodnoty Y** pod **přesunutím typu**nastavte 100%, aby ovládací prvek zůstal v rámci pravého dolního rohu v pevné vzdálenosti.

   ![Dynamické rozložení](../mfc/media/mfcdynamiclayout1.png "Dynamické rozložení")

1. Předpokládejme také, že máte ovládací prvek, který chcete rozšířit, když se dialogové okno rozbalí. Obvykle může uživatel rozbalit dialogové okno, aby rozšířil víceřádkový editbox, aby zvětšil velikost oblasti textu, nebo může rozšířit ovládací prvek seznamu, aby zobrazil více dat. Pro tento případ nastavte **typ změny velikosti** na obojí a nastavte **typ přesunutí** na žádný. Pak nastavte hodnoty **velikosti X** a **velikost Y** na 100.

   ![Nastavení dynamického rozložení](../mfc/media/mfcdynamiclayout2.png "Nastavení dynamického rozložení")

1. Experimentujte s dalšími hodnotami, které by mohly být vhodné pro vaše ovládací prvky. Dialogové okno s jedním řádkovým polem může mít **typ velikosti** nastavenou na hodnotu **Horizontal** , například.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Nastavení vlastností dynamického rozložení prostřednictvím kódu programu

Předchozí postup je užitečný pro zadání vlastností dynamického rozložení dialogového okna v době návrhu, ale pokud chcete řídit dynamické rozložení za běhu, můžete nastavit vlastnosti dynamického rozložení programově.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Programové nastavení vlastností dynamického rozložení

1. Vyhledejte nebo vytvořte místo v kódu implementace třídy dialogu, kde chcete zadat dynamické rozložení pro dialog. Například můžete chtít přidat metodu, jako je například `AdjustLayout` v dialogovém okně, a zavolat ji z míst, kde je nutné změnit rozložení. Je možné, že je nejprve volána z konstruktoru nebo po provedení změn v dialogovém okně.

1. Pro dialogové okno zavolejte [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), metodu třídy `CWnd`. `GetDynamicLayout` vrací ukazatel na objekt `CMFCDynamicLayout`.

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. Pro první ovládací prvek, do kterého chcete přidat dynamické chování, použijte statické metody třídy dynamického rozložení k vytvoření struktury [MoveSettings –](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) , která kóduje způsob, jakým má být ovládací prvek upravován. To provedete tak, že nejprve zvolíte vhodnou statickou metodu: [CMFCDynamicLayout:: MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout:: MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout:: MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)nebo [CMFCDynamicLayout:: MoveHorizontalAndVertical ](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Předáte procento pro horizontální nebo svislé aspekty přesunutí. Tyto statické metody vracejí nově vytvořený objekt MoveSettings –, který můžete použít k určení chování ovládacího prvku.

   Mějte na paměti, že 100 znamená, že při změně velikosti dialogového okna se mění velikost, což způsobí, že okraj ovládacího prvku zůstane od nového ohraničení pevně větší.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Proveďte stejnou věc pro chování velikosti, která používá typ [SizeSettings –](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) . Například chcete-li určit, že ovládací prvek při změně velikosti dialogového okna nezmění velikost, použijte následující kód:

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Přidejte ovládací prvek do správce dynamického rozložení pomocí metody [CMFCDynamicLayout:: AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) . Existují dvě přetížení různých způsobů určení požadovaného ovládacího prvku. Jeden vezme popisovač okna ovládacího prvku (HWND) a druhý vezme ID ovládacího prvku.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Opakujte pro každý ovládací prvek, který je třeba přesunout nebo změnit jeho velikost.

1. V případě potřeby lze použít metodu [CMFCDynamicLayout:: HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) k určení, zda je ovládací prvek již na seznamu ovládacích prvků, které jsou v souladu s dynamickými změnami rozložení, nebo metodou [CMFCDynamicLayout::-Empty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) k určení, zda existují ovládací prvky, které podléhají změnám.

1. Chcete-li povolit rozložení dialogového okna, zavolejte metodu [CWnd:: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) .

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. Při příštím změně velikosti dialogového okna se zavolá metoda [CMFCDynamicLayout:: upravit](../mfc/reference/cmfcdynamiclayout-class.md#adjust) , která nastavení skutečně aplikuje.

1. Chcete-li zakázat dynamické rozložení, zavolejte parametr [CWnd:: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) s hodnotou **false** jako parametr *bEnabled* .

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Nastavení dynamického rozložení programově ze souboru prostředků

1. Použijte metodu [CMFCDynamicLayout:: MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) k určení názvu prostředku v příslušném souboru skriptu prostředků (soubor. RC), který určuje informace o dynamickém rozložení, jak je uvedeno v následujícím příkladu:

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   Pojmenovaný prostředek musí odkazovat na dialog, který obsahuje informace o rozložení ve formě položky **AFX_DIALOG_LAYOUT** v souboru prostředků, jako v následujícím příkladu:

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>Viz také:

[CMFCDynamicLayout – třída](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[Třídy ovládacích prvků](../mfc/control-classes.md)<br/>
[Třídy dialogových oken](../mfc/dialog-box-classes.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Dynamické rozložení dialogového okna pro MFC v C++ jazyce Visual 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
