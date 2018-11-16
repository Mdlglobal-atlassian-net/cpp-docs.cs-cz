---
title: Přidat metodu
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: 23fb05e633713016b1f6289f73a916502736af10
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692682"
---
# <a name="add-a-method"></a>Přidat metodu

Můžete použít [Průvodce přidáním metody](#add-method-wizard) přidání metody do rozhraní ve vašem projektu. Pokud projekt obsahuje třídy související s rozhraním, Průvodce příliš upraví třídy.

**Přidání metody do objektu:**

1. V **zobrazení tříd**, rozbalte uzel projektu pro zobrazení rozhraní, ke kterému chcete přidat metodu.

   > [!NOTE]
   > Můžete také přidat metody do odesílacích rozhraních, která pokud je projekt s atributy, jsou umístěné pod uzlem knihovny.

1. Klikněte pravým tlačítkem na název rozhraní.

1. V místní nabídce zvolte **přidat**a klikněte na tlačítko **přidat metodu**.

1. V průvodci Přidat metody poskytují informace potřebné k vytvoření metody.

1. Zadejte nastavení jakékoli interface definition language pro tuto metodu v [IDL – atributy](#idl-attributes-add-method-wizard) stránky průvodce.

1. Vyberte **Dokončit** přidat metodu.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce přidáním metody](#add-method-wizard)
- [IDL – atributy, Průvodce přidáním metody](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Průvodce přidáním metody

Tohoto průvodce použijte k přidání metody rozhraní. V závislosti na typu projektu nebo do kterého přidáváte metodu typu rozhraní Průvodce zobrazí různé možnosti.

### <a name="names"></a>Názvy

- **Návratový typ**

  Datový typ vrácený metodou. `HRESULT` doporučuje se pro všechny typy rozhraní, protože poskytuje standardní způsob, jak vrátit chyby.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní|`HRESULT`. Jakákoliv.|
  |Vlastní rozhraní|`HRESULT`. Jakákoliv.|
  |Vlastní místní rozhraní|Zadejte vlastní návratový typ nebo vyberte ze seznamu.|
  |Dispinterface|Zadejte vlastní návratový typ nebo vyberte ze seznamu.|
  |Dispinterface ovládací prvek ActiveX knihovny MFC|Pokud implementujete základní metodu, je nastavena na hodnotu odpovídající návratový typ a nejde změnit. Pokud vyberete metodu z **název metody** seznam a vyberte **vlastní** pod **vyberte typ metody**, vyberte typ vrácené hodnoty ze seznamu.|

- **Název metody**

  Nastaví název metody.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Zadejte vlastní název metody.|
  |Dispinterface knihovny MFC|Zadejte název vlastní metody nebo vyberte název navrhované metody ze seznamu. Pokud název vyberete ze seznamu, zobrazí se v odpovídající hodnotu **návratový typ** pole a neměnný.|
  |Dispinterface ovládací prvek ActiveX knihovny MFC|Zadejte vlastní nebo vyberte některý z uložených metod [DoClick](../mfc/reference/colecontrol-class.md#doclick) a [aktualizovat](../mfc/reference/colecontrol-class.md#refresh). Další informace najdete v tématu [ovládací prvky MFC ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md).|

- **Typ metody**

  K dispozici pouze pro ovládací prvky ActiveX knihovny MFC. Pokud zadáte název metody ve **název metody** pole, namísto výběru metody ze seznamu, je toto políčko není k dispozici.

  Pokud vyberete jednu z metod v **název metody** seznamu, zvolte základní nebo vlastní implementaci.

  |Typ metody|Popis|
  |-----------------|-----------------|
  |**Stock**|Výchozí nastavení Vloží základní implementaci metody, vyberte v **název metody** seznamu. **Návratový typ** nejde změnit, pokud vyberete **akcie**.|
  |**Vlastní**|Vloží zástupné procedury implementace metody ve vybrané **název metody** seznamu. Pro typy vlastní metodu, můžete zadat vlastní návratový typ, nebo můžete vybrat jednu z **návratový typ** seznamu.|

- **Interní název**

  K dispozici pouze pro vlastní metody přidat odesílajícího rozhraní knihovny MFC. Nastaví název použitý v mapa odeslání, soubor hlaviček (.h) a soubor implementace (.cpp). Ve výchozím nastavení, tento název je stejný jako **název metody**. Můžete změnit název metody, pokud pracujete s odesílajícího rozhraní knihovny MFC nebo pokud přidáváte vlastní metodu odesílajícího rozhraní ovládací prvek ActiveX knihovny MFC.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a vlastní místní rozhraní|Není k dispozici.|
  |Dispinterface knihovny MFC|Ve výchozím nastavení má název metody. Můžete upravit interní název.|
  |Dispinterface ovládací prvek ActiveX knihovny MFC|Můžete nastavit jenom interní název vlastních metod. Uložených metod nepoužívejte interní název.|

- **Atributy parametru**

  Nastaví další atributy pro zadaný parametr v **název parametru**.

  |Atribut parametru|Popis|Povolené kombinace|
  |-------------------------|-----------------|--------------------------|
  |**V**|Označuje, že parametr je předán z volající procedury do volané procedury.|`in` Pouze<br /><br /> `in` a `out`|
  |**navýšení kapacity**|Označuje, že parametr ukazatel se vrátí z volané procedury do volající procedury (ze serveru do klienta).|`out` Pouze<br /><br /> `in` a `out`<br /><br /> `out` a `retval`|
  |**retval**|Označuje, že parametr přijímá návratovou hodnotu člena.|`retval` a `out`|

- **Typ parametru**

  Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

  Nastaví název parametru předávání metodu. Když zadáte název, vyberte **přidat** ho přidat do seznamu parametrů, které budou předány metodě. Pokud nezadáte název parametru, Průvodce přeskočí všechny atributy parametru (pouze ATL) nebo **typ parametru** výběry.

  Jakmile vyberete **přidat**, zobrazí se název parametru v **seznam parametrů**.

  > [!NOTE]
  > Pokud zadáte název parametru a pak vyberete **Dokončit** dřív, než vyberete **přidat**, není parametr metody přidán. Musíte najít metodu a ručně vložit parametr.

- **Add**

  Přidá parametr, který jste zadali v **název parametru**a její typ a atributy parametru do **seznam parametrů**. Vyberte **přidat** přidání parametru do seznamu.

- **odebrat**

  Odstraní parametr vyberete v **seznam parametrů** ze seznamu.

- **Seznam parametrů**

  Zobrazí všechny parametry a jejich typy, které jsou právě přidané do metody a modifikátory. Jak budete přidávat parametry, průvodce aktualizuje **seznam parametrů** zobrazíte každý parametr s jeho modifikátor a typem.

## <a name="idl-attributes-add-method-wizard"></a>IDL – atributy, Průvodce přidáním metody

Na této stránce Průvodce přidáním metody k určení nastavení jakékoli interface definition language (IDL) pro metodu.

- `id`

  Nastaví číselný Identifikátor, který identifikuje metodu. Další informace najdete v tématu [id](/windows/desktop/Midl/id) v *MIDL odkazu*.

  Toto pole není k dispozici pro vlastní rozhraní a není k dispozici pro odesílající rozhraní knihovny MFC.

- `call_as`

  Určuje název vzdálené metody, do které je možné mapovat tato metoda místní. Další informace najdete v tématu [call_as](/windows/desktop/Midl/call-as) v *MIDL odkazu*.

  Není k dispozici pro odesílající rozhraní knihovny MFC.

- `helpcontext`

  Určuje ID kontextu, který umožňuje uživateli zobrazit informace o této metodě v souboru nápovědy. Další informace najdete v tématu [helpcontext](/windows/desktop/Midl/helpcontext) v *MIDL odkazu*.

  Není k dispozici pro odesílající rozhraní knihovny MFC.

- `helpstring`

  Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje. To je standardně nastaven na "metoda *název metody*." Další informace najdete v tématu [helpstring](/windows/desktop/Midl/helpstring) v *MIDL odkazu*.

  Není k dispozici pro odesílající rozhraní knihovny MFC.

- **Další atributy**

  Není k dispozici pro odesílající rozhraní knihovny MFC.

  |Atribut|Popis|
  |---------------|-----------------|
  |`hidden`|Označuje, jestli metoda existuje, ale nebude se zobrazovat v prohlížeči uživatele. Další informace najdete v tématu [skryté](/windows/desktop/Midl/hidden) v *MIDL odkazu*.|
  |`source`|Označuje, že člen metoda je zdrojem událostí. Další informace najdete v tématu [zdroj](/windows/desktop/Midl/source) v *MIDL odkazu*.|
  |`local`|Určuje kompilátor MIDL o tom, že metoda není vzdálený. Další informace najdete v tématu [místní](/windows/desktop/Midl/local) v *MIDL odkazu*.|
  |`restricted`|Určuje metodu nejde volat libovolně. Další informace najdete v tématu [s omezeným přístupem](/windows/desktop/Midl/restricted) v *MIDL odkazu*.|
  |`vararg`|Určuje, že tato metoda přebírá proměnný počet argumentů. Jak toho dosáhnout, musí být posledním argumentem bezpečné pole `VARIANT` typ, který obsahuje zbývající argumenty. Další informace najdete v tématu [vararg](/windows/desktop/Midl/vararg) v *MIDL odkazu*.|
