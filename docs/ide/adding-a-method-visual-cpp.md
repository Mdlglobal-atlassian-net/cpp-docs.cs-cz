---
title: Přidání metody
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
ms.openlocfilehash: b0c8ddabc4ed08fd217545bad269f0b2e48dd49e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509538"
---
# <a name="add-a-method"></a>Přidání metody

[Průvodce přidáním metody](#add-method-wizard) lze použít k přidání metody do rozhraní v projektu. Pokud projekt obsahuje třídu přidruženou k rozhraní, průvodce změní také třídu.

**Přidání metody do objektu:**

1. V **zobrazení tříd**rozbalte uzel projektu pro zobrazení rozhraní, ke kterému chcete přidat metodu.

   > [!NOTE]
   > Můžete také přidat metody do odesílajícího rozhraní, které, pokud není projekt atributem, jsou umístěny pod uzlem knihovna.

1. Klikněte pravým tlačítkem myši na název rozhraní.

1. V místní nabídce klikněte na položku **Přidat**a poté zvolte možnost **Přidat metodu**.

1. V Průvodci přidáním metody zadejte informace k vytvoření metody.

1. Určete nastavení jazyka definice rozhraní pro tuto metodu na stránce [atributy IDL](#idl-attributes-add-method-wizard) průvodce.

1. Kliknutím na tlačítko **Dokončit** přidejte metodu.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce přidáním metody](#add-method-wizard)
- [IDL – atributy, Průvodce přidáním metody](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>Průvodce přidáním metody

Tento průvodce použijte k přidání metody do rozhraní. V závislosti na typu projektu nebo typu rozhraní, ke kterému přidáváte metodu, Průvodce zobrazí různé možnosti.

### <a name="names"></a>Názvy

- **Návratový typ**

  Datový typ vrácený metodou `HRESULT`je doporučen pro všechny typy rozhraní, protože poskytuje standardní způsob, jak vracet chyby.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní|`HRESULT`. Nedá měnit.|
  |Vlastní rozhraní|`HRESULT`. Nedá měnit.|
  |Místní vlastní rozhraní|Zadejte vlastní návratový typ nebo vyberte ze seznamu.|
  |Rozhraní|Zadejte vlastní návratový typ nebo vyberte ze seznamu.|
  |Odesílající rozhraní ovládacího prvku ActiveX knihovny MFC|Pokud implementujete uloženou metodu, návratový typ je nastaven na odpovídající hodnotu a nelze jej měnit. Pokud vyberete metodu ze seznamu **název metody** a v části **Vybrat typ metody**vyberte možnost **vlastní** , vyberte návratový typ ze seznamu.|

- **Název metody**

  Nastaví název metody.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a místní vlastní rozhraní|Zadejte vlastní název metody.|
  |Rozhraní MFC – odesílající|Zadejte vlastní název metody nebo v seznamu vyberte navrhovaný název metody. Pokud vyberete název ze seznamu, zobrazí se příslušná hodnota v poli **návratový typ** a nelze ji změnit.|
  |Odesílající rozhraní ovládacího prvku ActiveX knihovny MFC|Poskytněte vlastní nebo vyberte jednu z uložených metod [DoClick](../mfc/reference/colecontrol-class.md#doclick) a aktualizujte [](../mfc/reference/colecontrol-class.md#refresh). Další informace naleznete v tématu [ovládací prvky ActiveX knihovny MFC: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md).|

- **Typ metody**

  K dispozici pouze pro ovládací prvky MFC ActiveX. Pokud zadáte název metody do pole **název metody** , místo výběru metody ze seznamu není toto pole k dispozici.

  Pokud vyberete jednu z metod v seznamu **název metody** , vyberte buď skladovou implementaci, nebo vlastní implementaci.

  |Typ metody|Popis|
  |-----------------|-----------------|
  |**Kolejovými**|Výchozí nastavení Vloží uloženou implementaci metody, kterou jste vybrali v seznamu **název metody** . **Návratový typ** je nezměněný, pokud vyberete možnost **Sklad**.|
  |**Vlastní**|Vloží zástupnou implementaci metody vybrané v seznamu **název metody** . Pro vlastní typy metod můžete zadat svůj vlastní návratový typ nebo ho můžete vybrat ze seznamu **návratového typu** .|

- **Interní název**

  K dispozici pouze pro vlastní metody přidané do odesílajícího rozhraní knihovny MFC. Nastaví název použitý v mapě odeslání, v souboru hlaviček (. h) a v souboru implementace (. cpp). Ve výchozím nastavení je tento název stejný jako **název metody**. Pokud pracujete s odesílajícím rozhraním MFC nebo pokud přidáváte vlastní metodu pro odesílající rozhraní ovládacího prvku ActiveX knihovny MFC, můžete změnit název metody.

  |Typ rozhraní|Popis|
  |--------------------|-----------------|
  |Duální rozhraní ATL, vlastní rozhraní a místní vlastní rozhraní|Není k dispozici.|
  |Rozhraní MFC – odesílající|Ve výchozím nastavení se nastaví na název metody. Interní název můžete upravit.|
  |Odesílající rozhraní ovládacího prvku ActiveX knihovny MFC|Interní název lze nastavit pouze pro vlastní metody. Skladové metody nepoužívají interní název.|

- **Atributy parametru**

  Nastaví všechny další atributy pro parametr zadaný v **názvu parametru**.

  |Atribut parametru|Popis|Povolené kombinace|
  |-------------------------|-----------------|--------------------------|
  |**Pro**|Označuje, že parametr je předán z volající procedury do volané procedury.|`in`pouze<br /><br /> `in` a `out`|
  |**Mimo**|Označuje, že parametr ukazatele je vrácen z volané procedury do volající procedury (ze serveru do klienta).|`out`pouze<br /><br /> `in` a `out`<br /><br /> `out` a `retval`|
  |**Retval**|Označuje, že parametr přijímá návratovou hodnotu člena.|`retval` a `out`|

- **Typ parametru**

  Nastaví datový typ parametru. Vyberte typ ze seznamu.

- **Název parametru**

  Nastaví název parametru, který bude předávat vaše metoda. Po zadání názvu vyberte **Přidat** a přidejte ho do seznamu parametrů, které budou předávat vaše metoda. Pokud nezadáte název parametru, průvodce ignoruje všechny atributy parametrů (pouze ATL) nebo výběry **typu parametru** .

  Jakmile vyberete možnost **Přidat**, název parametru se zobrazí v **seznamu parametrů**.

  > [!NOTE]
  > Pokud zadáte název parametru a pak před výběrem **Přidat**, vyberte možnost **Dokončit** , parametr není přidán do metody. Je nutné najít metodu a vložit parametr ručně.

- **Add**

  Přidá parametr, který zadáte v **názvu parametru**, a jeho typ a atributy parametru na **seznam parametrů**. Vyberte **Přidat** a přidejte do seznamu parametr.

- **odebrat**

  Odstraní parametr, který jste vybrali v **seznamu parametrů** ze seznamu.

- **Seznam parametrů**

  Zobrazí všechny parametry a jejich modifikátory a typy aktuálně přidané pro metodu. Při přidávání parametrů průvodce aktualizuje **seznam parametrů** tak, aby zobrazoval každý parametr s jeho modifikátorem a typem.

## <a name="idl-attributes-add-method-wizard"></a>IDL – atributy, Průvodce přidáním metody

Tato stránka Průvodce přidáním metody slouží k určení libovolného nastavení jazyka IDL (Interface Definition Language) pro metodu.

- `id`

  Nastaví číselné ID, které identifikuje metodu. Další informace naleznete v tématu [ID](/windows/win32/Midl/id) v *odkazu MIDL*.

  Toto pole není k dispozici pro vlastní rozhraní a není k dispozici pro odesílající rozhraní knihovny MFC.

- `call_as`

  Určuje název vzdálené metody, na kterou lze mapovat tuto místní metodu. Další informace naleznete v tématu [call_as](/windows/win32/Midl/call-as) v *odkazu MIDL*.

  Není k dispozici pro odesílající rozhraní knihovny MFC.

- `helpcontext`

  Určuje ID kontextu, které uživateli umožňuje zobrazit informace o této metodě v souboru Help. Další informace naleznete v tématu [atribut HelpContext](/windows/win32/Midl/helpcontext) v *odkazu MIDL*.

  Není k dispozici pro odesílající rozhraní knihovny MFC.

- `helpstring`

  Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje. Ve výchozím nastavení se jedná o " *název metody*metody." Další informace naleznete v tématu [HelpString](/windows/win32/Midl/helpstring) v *odkazu MIDL*.

  Není k dispozici pro odesílající rozhraní knihovny MFC.

- **Další atributy**

  Není k dispozici pro odesílající rozhraní knihovny MFC.

  |Atribut|Popis|
  |---------------|-----------------|
  |`hidden`|Označuje, že metoda existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele. Další informace naleznete v tématu [Hidden](/windows/win32/Midl/hidden) v *odkazu MIDL*.|
  |`source`|Označuje, že člen metody je zdrojem událostí. Další informace naleznete v tématu [zdroj](/windows/win32/Midl/source) v *odkazu MIDL*.|
  |`local`|Určuje kompilátoru MIDL, že metoda není vzdálená. Další informace naleznete v tématu [místní](/windows/win32/Midl/local) v *odkazu MIDL*.|
  |`restricted`|Určuje, že metodu nelze volat libovolně. Další informace naleznete v tématu [omezeno](/windows/win32/Midl/restricted) v *odkazu MIDL*.|
  |`vararg`|Určuje, že metoda přijímá proměnný počet argumentů. Chcete-li to provést, musí být posledním argumentem bezpečné pole `VARIANT` typu, které obsahuje zbytek argumentů. Další informace naleznete v tématu [vararg](/windows/win32/Midl/vararg) v *odkazu MIDL*.|
