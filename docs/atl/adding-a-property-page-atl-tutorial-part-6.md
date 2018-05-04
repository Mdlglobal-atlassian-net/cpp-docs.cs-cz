---
title: Přidání stránky vlastností (ATL – tutoriál, část 6) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf7f0383697fbc1e23e179936a2616d1d236b5f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Přidání stránky vlastností (ATL – tutoriál, část 6)
Stránky vlastností jsou implementované jako samostatné objekty modelu COM, které mohly být sdílen, pokud je to nutné. V tomto kroku provedete následující úkoly a přidání stránky vlastností ovládacího prvku:  
  
-   Vytvoření prostředku stránky vlastností  
  
-   Přidání kódu k vytváření a správě jeho stránku vlastností  
  
-   Přidání stránky vlastností do ovládacího prvku  
  
## <a name="creating-the-property-page-resource"></a>Vytvoření prostředku stránky vlastností  
 K přidání stránky vlastností do vlastního ovládacího prvku, použijte Průvodce přidáním třídy ATL.  
  
#### <a name="to-add-a-property-page"></a>Přidání stránky vlastností  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na mnohoúhelníku.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat třídu**.  
  
3.  V seznamu šablon vyberte **stránka vlastností ATL** a klikněte na tlačítko **přidat**.  
  
4.  Jakmile se zobrazí stránka průvodce vlastnosti ATL, zadejte `PolyProp` jako **krátké** název.  
  
5.  Klikněte na tlačítko **řetězce** otevřete **řetězce** stránky a zadejte **& mnohoúhelníku** jako **název**.  
  
     **Název** vlastnosti stránky je řetězec, který se zobrazí na kartě pro tuto stránku. **Doc řetězec** je popis, který používá rámec vlastností uvést do stavu řádku nebo v popisu tlačítka. Všimněte si, že standardní rámec vlastností aktuálně nepoužívá tento řetězec, můžete ho nechte výchozí obsah. Nebude generovat **soubor nápovědy** v okamžiku, proto můžete odstranit položku z tohoto pole.  
  
6.  Klikněte na tlačítko **Dokončit**, a vytvoří se objekt stránku vlastností.  
  
 Následující tři soubory jsou vytvořeny:  
  
|Soubor|Popis|  
|----------|-----------------|  
|PolyProp.h|Obsahuje třídu C++ `CPolyProp`, který implementuje stránku vlastností.|  
|PolyProp.cpp|Obsahuje soubor PolyProp.h.|  
|PolyProp.rgs|Skript registru, který registruje objekt stránku vlastností.|  
  
 Rovněž jsou provedeny následující změny kódu:  
  
-   Položka mapování objektu v Polygon.cpp vkládá nové stránky vlastností.  
  
-   `PolyProp` Třída je přidat do souboru Polygon.idl.  
  
-   Nový soubor skriptu registru PolyProp.rgs se přidá do projektu prostředků.  
  
-   Pole šablony dialogového okna se přidá do projektu prostředků pro stránku vlastností.  
  
-   Vlastnost řetězce, které jste zadali budou přidány do tabulky řetězec prostředku.  
  
 Nyní přidejte pole, která se má zobrazit na stránce vlastností.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Chcete-li přidat pole na stránce vlastností  
  
1.  V Průzkumníku řešení poklikejte na soubor Polygon.rc prostředků. Tím se otevře zobrazení zdrojů.  
  
2.  V zobrazení zdrojů rozbalte uzel dialogové okno a dvakrát klikněte na IDD_POLYPROP. Všimněte si, zobrazí se okno, které je prázdný, s výjimkou štítek, který se dozvíte, chcete-li vložit vaše ovládací prvky.  
  
3.  Vyberte tohoto popisku a změňte ho na `Sides:` změnou **popisek** textu v **vlastnosti** okno.  
  
4.  Změna velikosti pole popisku tak, aby odpovídal velikost textu.  
  
5.  Přetáhněte ovládací prvek upravit z panelu nástrojů vpravo popisku.  
  
6.  Nakonec změnit **ID** ovládacích prvků pro úpravy k `IDC_SIDES` pomocí okna Vlastnosti.  
  
 Tím se dokončí proces vytváření prostředků stránku vlastností.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Přidání kódu k vytváření a správě jeho stránku vlastností  
 Teď, když jste vytvořili prostředek vlastností stránky, budete muset psát kód implementace.  
  
 Nejprve povolit `CPolyProp` třída nastavit počet stran v objektu při **použít** stisknutí tlačítka.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Chcete-li upravit funkce použít, chcete-li nastavit počet stran  
  
1.  Nahraďte `Apply` funkce v PolyProp.h následujícím kódem:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Stránky vlastností může mít více než jednoho klienta, které jsou k němu připojen najednou, proto `Apply` funkce kolem v cyklu a volá `put_Sides` v každém klientovi s hodnotou načtena z textové pole. Používáte [CComQIPtr](../atl/reference/ccomqiptr-class.md) třídy, která provádí `QueryInterface` na každém objektu získat `IPolyCtl` rozhraní z **IUnknown** rozhraní (uložené v `m_ppUnk` pole).  
  
 Kód kontroluje nyní tohoto nastavení `Sides` vlastnost ve skutečnosti fungovala. Pokud se nezdaří, kód zobrazí okno zobrazení Podrobnosti o chybě z **IErrorInfo** rozhraní. Obvykle kontejner požádá objekt pro **ISupportErrorInfo** rozhraní a volání `InterfaceSupportsErrorInfo` first, abyste zjistili, zda objekt podporuje nastavení informace o chybě. Můžete přeskočit tuto úlohu.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) vám pomůže pomocí automaticky zpracování počítání odkazů, takže není nutné volat `Release` na rozhraní. `CComBSTR` pomáhá s `BSTR` zpracování, takže není nutné k provedení konečné `SysFreeString` volání. Můžete také použít různé třídy převod řetězce, tak můžete převést `BSTR` v případě potřeby (to je důvod, proč `USES_CONVERSION` makro je na začátku funkce).  
  
 Musíte taky nastavit příznak změny její stránku vlastností s údajem, že **použít** tlačítko by měla být povolená. K tomu dojde, když uživatel změní hodnotu v **stranách** textové pole.  
  
#### <a name="to-handle-the-apply-button"></a>Pro zpracování tlačítka použít  
  
1.  V zobrazení tříd, klikněte pravým tlačítkem na CPolyProp a klikněte na **vlastnosti** v místní nabídce.  
  
2.  V okně vlastností klikněte **události** ikonu.  
  
3.  Rozbalte `IDC_SIDES` uzlu v seznamu událostí.  
  
4.  Vyberte `EN_CHANGE`a v rozevírací nabídce vpravo klikněte na tlačítko  **\<Přidat > OnEnChangeSides**. `OnEnChangeSides` Obslužná rutina deklarace budou přidány do Polyprop.h a implementaci obslužné rutiny na Polyprop.cpp.  
  
 V dalším kroku upravíte obslužná rutina.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Chcete-li změnit metodu OnEnChangeSides  
  
1.  Přidejte následující kód v Polyprop.cpp k `OnEnChangeSides` – metoda (odstranění kód, který průvodce put existuje):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` bude volána při **wm_command –** je zpráva odeslána s **EN_CHANGE** oznámení pro `IDC_SIDES` ovládacího prvku. `OnEnChangeSides` pak zavolá `SetDirty` a předá `TRUE` udávajících vlastnost stránky je nyní nekonzistentní a **použít** tlačítko by měla být povolená.  
  
## <a name="adding-the-property-page-to-the-control"></a>Přidání stránky vlastností do ovládacího prvku  
 Průvodce přidáním třídy ATL a Průvodce stránky vlastností knihovny ATL nepřidávejte stránku vlastností do vlastního ovládacího prvku pro vás automaticky, vzhledem k tomu může být více ovládacích prvků ve vašem projektu. Musíte přidat položku do mapa vlastností ovládacího prvku.  
  
#### <a name="to-add-the-property-page"></a>Přidání stránky vlastností  
  
1.  Otevřete PolyCtl.h a přidejte tento řádek do mapy vlastností:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Mapa vlastností ovládacího prvku nyní vypadat třeba takto:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Může jste přidali `PROP_PAGE` makro s CLSID vlastností stránky, ale pokud použijete `PROP_ENTRY` makro, jak je vidět, `Sides` hodnota vlastnosti je uložena také při uložení ovládacího prvku.  
  
 Tři parametry makro jsou popis vlastnosti, DISPID vlastnosti a CLSID vlastností stránky, která má vlastnost na něm. To je užitečné, pokud například načítání ovládacího prvku do jazyka Visual Basic a nastavit počet stran v době návrhu. Protože je uložen počet stran, při opětovném načtení projektu jazyka Visual Basic, počet stran se obnoví.  
  
## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku  
 Teď sestavení tohoto ovládacího prvku a vložení do kontejner testů ovládacích prvků ActiveX. V testu kontejneru na **upravit** nabídky, klikněte na tlačítko **objektu třídy PolyCtl**. Zobrazí se stránka Vlastnosti; klikněte **mnohoúhelníku** kartě.  
  
 **Použít** tlačítko zpočátku je zakázané. Začněte psát hodnotu v **stranách** pole a **použít** se zpřístupní tlačítko. Po dokončení zadáte hodnotu, klikněte na tlačítko **použít** tlačítko. Změny zobrazení ovládacího prvku a **použít** tlačítko znovu je zakázané. Zkuste zadat neplatnou hodnotu. Zobrazí se okno se zprávou obsahující popis chyby, který nastavíte z `put_Sides` funkce.  
  
 V dalším kroku umístíte ovládacího prvku na webové stránce.  
  
 [Zpátky ke kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [na krok 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

