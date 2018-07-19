---
title: Přidání stránky vlastností (ATL – tutoriál, část 6) | Dokumentace Microsoftu
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
ms.openlocfilehash: 32b89b36318800ff35bc78fee35f094f75bdf36e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848688"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Přidání stránky vlastností (ATL – tutoriál, část 6)
Stránky vlastností jsou implementované jako samostatné objekty modelu COM, které zajistí, aby sdílet, pokud je to nutné. V tomto kroku provedete následující kroky přidání stránky vlastností do ovládacího prvku:  
  
-   Vytváří se prostředek stránky vlastností  
  
-   Přidání kódu k vytváření a správě stránky vlastností  
  
-   Přidání stránky vlastností do ovládacího prvku  
  
## <a name="creating-the-property-page-resource"></a>Vytváří se prostředek stránky vlastností  
 Přidání stránky vlastností do ovládacího prvku, použijte Průvodce přidáním třídy ATL.  
  
#### <a name="to-add-a-property-page"></a>Přidání stránky vlastností  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem myši na mnohoúhelník.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.  
  
3.  V seznamu šablon vyberte **stránka vlastností knihovny ATL** a klikněte na tlačítko **přidat**.  
  
4.  Jakmile se zobrazí Průvodce stránkou vlastností ATL, zadejte *PolyProp* jako **krátký** název.  
  
5.  Klikněte na tlačítko **řetězce** otevřít **řetězce** stránku a zadejte **& mnohoúhelníku** jako **Title**.  
  
     **Název** vlastnosti stránky je řetězec, který se zobrazí na kartě pro danou stránku. **Řetězec Doc** je popis, který používá rámec vlastnosti uvést do stavu řádku nebo v popisu tlačítka. Všimněte si, že rámec standardní vlastnosti aktuálně nepoužívá tento řetězec, takže ho můžete nechat výchozí obsah. Nebude generovat **soubor nápovědy** v okamžiku, proto můžete odstranit položku do tohoto textového pole.  
  
6.  Klikněte na tlačítko **Dokončit**, a vytvoří se objekt stránky vlastností.  
  
 Následující tři soubory jsou vytvořeny:  
  
|Soubor|Popis|  
|----------|-----------------|  
|PolyProp.h|Obsahuje třídu C++ `CPolyProp`, který implementuje stránku vlastností.|  
|PolyProp.cpp|Zahrnuje soubor PolyProp.h.|  
|PolyProp.rgs|Skript registru, která se registruje objekt stránky vlastností.|  
  
 Také budou provedeny následující změny kódu:  
  
-   Nové stránky vlastností se přidá do mapy vstupního objektu v Polygon.cpp.  
  
-   `PolyProp` Třídy se přidá do souboru Polygon.idl.  
  
-   Přidá nový soubor skriptu registru PolyProp.rgs prostředku projektu.  
  
-   Šablony dialogového okna se přidá do projektu prostředků pro stránku vlastností.  
  
-   Vlastnost řetězce, které jste zadali, se přidají do tabulce zdrojových řetězců.  
  
 Nyní přidejte pole, která se má zobrazit na stránce vlastností.  
  
#### <a name="to-add-fields-to-the-property-page"></a>Přidání polí na stránce vlastností  
  
1.  V Průzkumníku řešení poklikejte na soubor prostředků Polygon.rc. Otevře se zobrazení prostředků.  
  
2.  V okně zobrazení prostředků rozbalte uzel dialogové okno a dvakrát klikněte na panel IDD_POLYPROP. Všimněte si, že je dialogové okno, které se zobrazí prázdný s výjimkou, že musíte vložte své ovládací prvky popisek.  
  
3.  Vyberte tento popisek a změňte ho na čtení `Sides:` změnou **titulek** textu v **vlastnosti** okna.  
  
4.  Změnit velikost pole popisku, tak, aby velikost textu.  
  
5.  Přetáhněte ovládací prvek upravit z panelu nástrojů napravo od popisku.  
  
6.  Nakonec změňte **ID** ovládacích prvků pro úpravy k `IDC_SIDES` pomocí okna Vlastnosti.  
  
 Tím dokončíte proces vytváření prostředků stránky vlastností.  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>Přidání kódu k vytváření a správě stránky vlastností  
 Teď, když jste vytvořili prostředek stránky vlastností, budete muset psát kód implementace.  
  
 Nejprve povolit `CPolyProp` třídy nastavit počet stran v objektu při **použít** stisknutí tlačítka.  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Chcete-li změnit funkci použít k nastavení počtu stran  
  
1.  Nahradit `Apply` funkce v PolyProp.h následujícím kódem:  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 Na stránce vlastnosti může být více než jednoho klienta k němu připojená najednou, proto `Apply` funkce smyčky kolem a volá `put_Sides` v každém klientovi s hodnotou načtena z pole pro úpravy. Používáte [CComQIPtr](../atl/reference/ccomqiptr-class.md) třídu, která provádí `QueryInterface` na každém objektu získat `IPolyCtl` rozhraní z `IUnknown` rozhraní (uložené v `m_ppUnk` pole).  
  
 Kód kontroluje nyní také toto nastavení `Sides` vlastnost skutečně pracoval. Pokud selže, kód zobrazí okno se zprávou zobrazení Podrobnosti o chybě poskytnuté `IErrorInfo` rozhraní. Obvykle kontejner požádá objekt pro `ISupportErrorInfo` rozhraní a volání `InterfaceSupportsErrorInfo` první, chcete-li zjistit, zda objekt podporuje nastavení informace o chybě. Přeskočit tuto úlohu.  
  
 [CComPtr](../atl/reference/ccomptr-class.md) pomáhá tím, že automaticky zpracování, počítání odkazů, takže není potřeba volat `Release` na rozhraní. `CComBSTR` vám pomůže se zpracováním, BSTR, takže není nutné k provedení konečné `SysFreeString` volání. Použijete také jeden z různých tříd převodu řetězců, tak v případě potřeby (to je důvod, proč je makro USES_CONVERSION na začátku funkce) můžete převést BSTR.  
  
 Také je nutné nastavit příznak změny na stránce vlastností k označení, že **použít** tlačítko by měla být povolená. K tomu dojde, když uživatel změní hodnotu **strany** textové pole.  
  
#### <a name="to-handle-the-apply-button"></a>Pro zpracování tlačítka použít  
  
1.  V zobrazení tříd klikněte pravým tlačítkem myši na CPolyProp a klikněte na tlačítko **vlastnosti** v místní nabídce.  
  
2.  V okně Vlastnosti klikněte na tlačítko **události** ikonu.  
  
3.  Rozbalte `IDC_SIDES` uzel v seznamu událostí.  
  
4.  Vyberte `EN_CHANGE`a z rozevírací nabídky na pravé straně, klikněte na tlačítko  **\<Přidat > OnEnChangeSides**. `OnEnChangeSides` Polyprop.h a implementaci obslužné rutiny pro Polyprop.cpp se přidá deklarace obslužné rutiny.  
  
 V dalším kroku upravíte obslužné rutiny.  
  
#### <a name="to-modify-the-onenchangesides-method"></a>Chcete-li změnit OnEnChangeSides – metoda  
  
1.  Přidejte následující kód v Polyprop.cpp k `OnEnChangeSides` – metoda (odstranění veškerý kód, který ukládat průvodce):  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` bude volána při odeslání wm_command – zprávy s oznámením EN_CHANGE pro `IDC_SIDES` ovládacího prvku. `OnEnChangeSides` pak zavolá `SetDirty` a předává TRUE označíte, na stránce vlastností je nyní změny a **použít** tlačítko by měla být povolená.  
  
## <a name="adding-the-property-page-to-the-control"></a>Přidání stránky vlastností do ovládacího prvku  
 Průvodce přidáním třídy ATL a Průvodce stránkou vlastností ATL nepřidávejte na stránce vlastností do ovládacího prvku za vás automaticky, protože může být více ovládacích prvků ve vašem projektu. Je potřeba přidat položku do mapy vlastností ovládacího prvku.  
  
#### <a name="to-add-the-property-page"></a>Přidání stránky vlastností  
  
1.  Otevřete souboru PolyCtl.h a přidejte tento řádek do mapy vlastností:  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 Mapy vlastností ovládacího prvku nyní vypadá takto:  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 Může mít přidán PROP_PAGE makro s identifikátorem CLSID stránky vlastností, ale když použijete – makro PROP_ENTRY, jak je vidět, `Sides` hodnota vlastnosti se také uloží při uložení ovládacího prvku.  
  
 Tři parametry makra jsou vlastnosti popis, DISPID vlastnost a CLSID stránky vlastností, který má vlastnost. To je užitečné, pokud například načíst ovládací prvek do jazyka Visual Basic a nastavit počet stran v době návrhu. Vzhledem k tomu, že počet stran je uložen, pokud znovu načíst projekt v jazyce Visual Basic, počet stran se obnoví.  
  
## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku  
 Nyní sestavení ovládacího prvku a vložte ji do kontejner testů ovládacích prvků ActiveX. V kontejneru testů na **upravit** nabídky, klikněte na tlačítko **objekt PolyCtl třídy**. Zobrazí se stránka vlastností. Klikněte na tlačítko **mnohoúhelníku** kartu.  
  
 **Použít** tlačítko je zpočátku zakázáno. Začněte psát hodnotu **strany** pole a **použít** tlačítko bude přístupné. Jakmile dokončíte zadávání hodnoty, klikněte na tlačítko **použít** tlačítko. Ovládací prvek zobrazení změn a **použít** znovu je tlačítko neaktivní. Zkuste zadat neplatnou hodnotu. Zobrazí se okno se zprávou obsahující popis chyby, které jste nastavili z `put_Sides` funkce.  
  
 V dalším kroku umístíte ovládacího prvku na webové stránce.  
  
 [Zpátky ke kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [ke kroku 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

