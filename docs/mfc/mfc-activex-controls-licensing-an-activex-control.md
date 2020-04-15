---
title: 'MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX'
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364608"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX

Podpora licencování, volitelná funkce ovládacích prvků ActiveX, umožňuje řídit, kdo je schopen používat nebo distribuovat ovládací prvek. (Další informace o problémech s licencováním najdete v tématu Problémy s licencováním [v inovaci existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Tento článek popisuje následující témata:

- [Přehled licencování ovládacího prvku ActiveX](#_core_overview_of_activex_control_licensing)

- [Vytvoření licencovaného ovládacího prvku](#_core_creating_a_licensed_control)

- [Podpora licencí](#_core_licensing_support)

- [Přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Ovládací prvky ActiveX, které implementují licencování, umožňují jako vývojářovládacího prvku určit, jak budou ostatní uživatelé používat ovládací prvek ActiveX. Můžete poskytnout ovládacíprvek a . LIC se souhlasem, že kupující může distribuovat kontrolu, ale ne . LIC, s aplikací, která používá ovládací prvek. To zabrání uživatelům této aplikace v psaní nových aplikací, které používají ovládací prvek, bez předchozílicencování ovládacího prvku od vás.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>Přehled licencování ovládacího prvku ActiveX

Chcete-li poskytnout podporu licencování ovládacích prvků ActiveX, poskytuje třída [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) implementaci několika funkcí v `IClassFactory2` rozhraní: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, a `IClassFactory2::CreateInstanceLic`. Když vývojář aplikace kontejneru požádá o vytvoření instance ovládacího `GetLicInfo` prvku, je provedeno volání k ověření, že ovládací prvek . LIC soubor je k dispozici. Pokud je ovládací prvek licencován, instance ovládacího prvku může být vytvořena a umístěna do kontejneru. Poté, co vývojář dokončil vytváření aplikace kontejneru, je `RequestLicKey`provedeno jiné volání funkce , tentokrát do . Tato funkce vrátí licenční klíč (jednoduchý řetězec znaků) do aplikace kontejneru. Vrácený klíč je pak vložen do aplikace.

Následující obrázek ukazuje ověření licence ovládacího prvku ActiveX, který bude použit při vývoji kontejnerové aplikace. Jak již bylo zmíněno dříve, vývojář aplikace kontejneru musí mít správné . LIC soubor nainstalovaný ve vývojovém počítači k vytvoření instance ovládacího prvku.

![Licencované ovládací prvek ActiveX ověřený při vývoji](../mfc/media/vc374d1.gif "Licencované ovládací prvek ActiveX ověřený při vývoji") <br/>
Ověření licencovaného ovládacího prvku ActiveX během vývoje

Další proces, který je znázorněn na následujícím obrázku, nastane, když koncový uživatel spustí aplikaci kontejneru.

Při spuštění aplikace je obvykle nutné vytvořit instanci ovládacího prvku. Kontejner toho dosáhne voláním , `CreateInstanceLic`předáním vloženého licenčního klíče jako parametru. Poté se provádí porovnání řetězců mezi vloženým licenčním klíčem a vlastní kopií licenčního klíče ovládacího prvku. Pokud je shoda úspěšná, je vytvořena instance ovládacího prvku a aplikace pokračuje v normálním spuštění. Všimněte si, že . LIC soubor nemusí být přítomen na počítači uživatele ovládacího prvku.

![Licencovaný ovládací prvek ActiveX ověřený při spuštění](../mfc/media/vc374d2.gif "Licencovaný ovládací prvek ActiveX ověřený při spuštění") <br/>
Ověření licencovaného ovládacího prvku ActiveX během provádění

Řízení licencí se skládá ze dvou základních součástí: specifický kód v dll implementace ovládacího prvku a licenční soubor. Kód se skládá ze dvou (nebo případně tří) volání funkcí a znakového řetězce, dále jen "licenční řetězec", který obsahuje oznámení o autorských právech. Tato volání a licenční řetězec se nacházejí v implementaci ovládacího prvku (. CPP). Licenční soubor generovaný Průvodcem ovládacím prvkem ActiveX je textový soubor s prohlášením o autorských právech. Je pojmenován pomocí názvu projektu s . LIC rozšíření, například SAMPLE. Lic. Licencovaný ovládací prvek musí být doprovázen licenčním souborem, pokud je nutné použít návrh.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>Vytvoření licencovaného ovládacího prvku

Při použití Průvodce ovládacím prvkem ActiveX k vytvoření rozhraní ovládacího prvku je snadné zahrnout podporu licencování. Pokud určíte, že ovládací prvek by měl mít licenci za běhu, Průvodce řízením ActiveX přidá kód do třídy ovládacího prvku pro podporu licencování. Kód se skládá z funkcí, které používají klíč a licenční soubor pro ověření licence. Tyto funkce lze také upravit přizpůsobit řízení licencí. Další informace o přizpůsobení licence naleznete [v tématu Přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control) dále v tomto článku.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Přidání podpory pro licencování pomocí Průvodce ovládacím prvkem ActiveX při vytváření řídicího projektu

1. Použijte pokyny v [části Vytvoření ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md). Stránka **Nastavení aplikace** Průvodce ovládacím prvkem ActiveX obsahuje možnost vytvoření ovládacího prvku pomocí licence za běhu.

Průvodce řízením ActiveX nyní generuje rozhraní ovládacího prvku ActiveX, které zahrnuje základní podporu licencování. Podrobné vysvětlení licenčního kódu naleznete v dalším tématu.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>Podpora licencí

Pokud pomocí Průvodce řízením ActiveX přidáte podporu licencí do ovládacího prvku ActiveX, Průvodce ovládacím prvkem ActiveX přidá kód, který deklaruje a implementuje možnost licencování, je přidán do záhlaví ovládacího prvku a souborů implementace. Tento kód se `VerifyUserLicense` skládá z `GetLicenseKey` členské funkce a členské funkce, které přepsat výchozí implementace nalezené v [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Tyto funkce načíst a ověřit kontrolní licenci.

> [!NOTE]
> Třetí členská `VerifyLicenseKey` funkce není generována Průvodcem ovládacího prvku ActiveX, ale může být přepsána a přizpůsobit chování ověřování licenčního klíče.

Tyto členské funkce jsou:

- [Ověřitlicenci uživatele](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Ověří, zda ovládací prvek umožňuje použití v době návrhu kontrolou přítomnosti souboru licence ovládacího prvku. Tato funkce je volána rámcem `IClassFactory2::GetLicInfo` `IClassFactory::CreateInstanceLic`jako součást zpracování a .

- [Klíč GetLicense](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Požaduje jedinečný klíč z řídicí dll. Tento klíč je vložen do aplikace kontejneru a `VerifyLicenseKey`později použit ve spojení s , k vytvoření instance ovládacího prvku. Tato funkce je volána rámci `IClassFactory2::RequestLicKey`jako součást zpracování .

- [Ověřitlicenční klíč](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Ověří, zda je vložený klíč a jedinečný klíč ovládacího prvku stejný. To umožňuje kontejneru vytvořit instanci ovládacího prvku pro jeho použití. Tato funkce je volána v `IClassFactory2::CreateInstanceLic` rámci jako součást zpracování a může být přepsána, aby poskytovala přizpůsobené ověření licenčního klíče. Výchozí implementace provádí porovnání řetězců. Další informace naleznete [v tématu Přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)dále v tomto článku.

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>Změny souboru záhlaví

Průvodce ovládacím prvkem ActiveX umístí následující kód do souboru záhlaví ovládacího prvku. V tomto příkladu jsou `CSampleCtrl`deklarovány dvě členské funkce objektu `factory` , jedna, která ověřuje přítomnost ovládacího prvku . LIC a další, který načte licenční klíč, který má být použit v aplikaci obsahující ovládací prvek:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>Změny implementačního souboru

Průvodce ovládacím prvkem ActiveX umístí následující dva příkazy do souboru implementace ovládacího prvku, aby deklaroval název licenčního souboru a licenční řetězec:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> Pokud změníte `szLicString` jakýmkoli způsobem, musíte také upravit první řádek v ovládacím prvku . LIC soubor nebo licencování nebude fungovat správně.

Průvodce ovládacím prvkem ActiveX umístí do souboru implementace ovládacího prvku následující kód, který definuje třídu ovládacího prvku a `VerifyUserLicense` `GetLicenseKey` funkce:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

**Nakonec Průvodce ovládacím prvkem ActiveX** upraví projekt ovládacího prvku . IDL. **Licencované** klíčové slovo je přidáno do deklarace coclass ovládacího prvku, jako v následujícím příkladu:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>Přizpůsobení licencování ovládacího prvku ActiveX

Vzhledem `GetLicenseKey`k `VerifyLicenseKey` tomu, `VerifyUserLicense`, a jsou deklarovány jako virtuální členské funkce třídy factory ovládacího prvku, můžete přizpůsobit chování licencování ovládacího prvku.

Můžete například zadat několik úrovní licencování pro ovládací `VerifyUserLicense` `VerifyLicenseKey` prvek přepsáním nebo členské funkce. Uvnitř této funkce můžete nastavit, které vlastnosti nebo metody jsou uživateli vystaveny podle úrovně licence, kterou jste zjistili.

Můžete také přidat kód `VerifyLicenseKey` do funkce, která poskytuje vlastní metodu pro informování uživatele, že vytvoření ovládacího prvku se nezdařilo. Například v `VerifyLicenseKey` členské funkci můžete zobrazit okno se zprávou oznamující, že se nepodařilo inicializovat ovládací prvek a proč.

> [!NOTE]
> Dalším způsobem, jak přizpůsobit ověření licence ovládacího prvku ActiveX, je `AfxVerifyLicFile`zkontrolovat v registrační databázi konkrétní klíč registru namísto volání . Příklad výchozí implementace naleznete v tomto článku v části [Změny souboru implementace.](#_core_implementation_file_modifications)

Další informace o problémech s licencováním naleznete v tématu Problémy s licencováním [v tématu Upgrade existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../mfc/reference/mfc-activex-control-wizard.md)
