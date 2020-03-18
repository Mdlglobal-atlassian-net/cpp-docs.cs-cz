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
ms.openlocfilehash: b08abdc0e2c17cb61c0c6a14cd712ec32ea816bd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438016"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX

Podpora licencování, volitelná funkce ovládacích prvků ActiveX, umožňuje řídit, kdo může ovládací prvek používat nebo distribuovat. (Další diskuzi o problémech s licencováním najdete v tématu věnovaném licenčním problémům při [upgradu existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX je starší verze technologie, která by se neměla používat pro nový vývoj. Další informace o moderních technologiích, které nahrazují prvky ActiveX, naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Tento článek popisuje v následujících tématech:

- [Přehled licencování ovládacích prvků ActiveX](#_core_overview_of_activex_control_licensing)

- [Vytvoření licencovaného ovládacího prvku](#_core_creating_a_licensed_control)

- [Podpora licencování](#_core_licensing_support)

- [Přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Ovládací prvky ActiveX, které implementují licencování, umožňují vám jako vývojář ovládacího prvku určit, jak budou jiní uživatelé používat ovládací prvek ActiveX. Nákupčímu ovládacího prvku poskytujete ovládací prvek a. Soubor. LIC s dohodou o tom, že kupující může tento ovládací prvek distribuovat, ale ne. Soubor. LIC s aplikací, která používá ovládací prvek. Tím zabráníte uživatelům této aplikace v psaní nových aplikací, které ovládací prvek používají, a to bez předchozího licencování řízení od vás.

##  <a name="_core_overview_of_activex_control_licensing"></a>Přehled licencování ovládacích prvků ActiveX

Pro zajištění podpory licencování pro ovládací prvky ActiveX poskytuje třída [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) implementaci pro několik funkcí v rozhraní `IClassFactory2`: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`a `IClassFactory2::CreateInstanceLic`. Pokud vývojář aplikace kontejneru vytvoří požadavek na vytvoření instance ovládacího prvku, je provedeno volání `GetLicInfo` pro ověření, zda ovládací prvek. Soubor LIC je přítomen. Pokud je ovládací prvek licencován, lze vytvořit instanci ovládacího prvku a umístit jej do kontejneru. Poté, co vývojář dokončí konstrukci aplikace kontejneru, je provedena další volání funkce, tentokrát `RequestLicKey`. Tato funkce vrátí licenční klíč (jednoduchý řetězec znaků) do aplikace typu kontejner. Vrácený klíč se pak vloží do aplikace.

Následující obrázek ukazuje ověření licence ovládacího prvku ActiveX, který bude použit během vývoje aplikace typu kontejner. Jak bylo zmíněno dříve, musí mít vývojář aplikace kontejneru správný. Soubor LIC nainstalovaný ve vývojovém počítači pro vytvoření instance ovládacího prvku.

![Licencovaný ovládací prvek ActiveX ověřený při vývoji](../mfc/media/vc374d1.gif "Licencovaný ovládací prvek ActiveX ověřený při vývoji") <br/>
Ověření licencovaného ovládacího prvku ActiveX během vývoje

Další postup zobrazený na následujícím obrázku nastane, pokud koncový uživatel spustí aplikaci kontejneru.

Po spuštění aplikace se obvykle musí vytvořit instance ovládacího prvku. Kontejner to dosahuje tak, že vyvolá volání `CreateInstanceLic`a předání vloženého licenčního klíče jako parametru. Pak je provedeno porovnání řetězců mezi vloženým licenčním klíčem a vlastní kopií licenčního klíče ovládacího prvku. Je-li shoda úspěšná, je vytvořena instance ovládacího prvku a aplikace bude nadále spouštěna normálně. Všimněte si, že. Soubor LIC nemusí být přítomen v počítači uživatele ovládacího prvku.

![Licencovaný ovládací prvek ActiveX byl ověřen při spuštění](../mfc/media/vc374d2.gif "Licencovaný ovládací prvek ActiveX byl ověřen při spuštění") <br/>
Ověření licencovaného ovládacího prvku ActiveX během provádění

Licencování ovládacích prvků se skládá ze dvou základních komponent: konkrétní kód v knihovně DLL implementace ovládacího prvku a soubor s licencí. Kód se skládá ze dvou (nebo případně tří) volání funkcí a řetězce znaků, dále označovaného jako "řetězec licence", který obsahuje oznámení o autorských právech. Tato volání a licenční řetězec se nacházejí v implementaci ovládacího prvku (. CPP). Soubor s licencí generovaný průvodcem ovládacím prvkem ActiveX je textový soubor s prohlášením o autorských právech. Je pojmenována pomocí názvu projektu s. Přípona LIC, například SAMPLE. LIC. Licencovaný ovládací prvek musí být doplněn licenčním souborem, pokud je potřeba použití v době návrhu.

##  <a name="_core_creating_a_licensed_control"></a>Vytvoření licencovaného ovládacího prvku

Když použijete Průvodce ovládacím prvkem ActiveX k vytvoření architektury ovládacího prvku, je snadné zahrnout podporu licencování. Pokud určíte, že má ovládací prvek mít licenci run-time, Průvodce ovládacím prvkem ActiveX přidá do třídy ovládacího prvku kód pro podporu licencování. Kód se skládá z funkcí, které pro ověření licence používají klíč a soubor s licencí. Tyto funkce lze také upravit, aby bylo možné přizpůsobit licencování ovládacích prvků. Další informace o přizpůsobení licencí najdete v části [přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control) dále v tomto článku.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Přidání podpory pro licencování pomocí Průvodce ovládacím prvkem ActiveX při vytváření projektu ovládacího prvku

1. Použijte pokyny v [tématu Vytvoření ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md). Stránka **nastavení aplikace** v průvodci ovládacím prvkem ActiveX obsahuje možnost vytvořit ovládací prvek s licencí run-time.

Průvodce ovládacím prvkem ActiveX nyní vygeneruje rozhraní ovládacího prvku ActiveX, které zahrnuje základní licenční podporu. Podrobné vysvětlení licenčního kódu najdete v dalším tématu.

##  <a name="_core_licensing_support"></a>Podpora licencování

Použijete-li Průvodce ovládacím prvkem ActiveX k přidání podpory licencování do ovládacího prvku ActiveX, Průvodce ovládacím prvkem ActiveX přidá kód, který deklaruje a implementuje možnost licencování, do hlavičky ovládacího prvku a implementační soubory. Tento kód se skládá z `VerifyUserLicense` členské funkce a členská funkce `GetLicenseKey`, která přepíše výchozí implementace nalezené v [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Tyto funkce načtou a ověřují licenci pro řízení.

> [!NOTE]
>  Třetí členská `VerifyLicenseKey` funkce není generována průvodcem ovládacím prvkem ActiveX, ale může být přepsána k přizpůsobení chování ověření licenčního klíče.

Tyto členské funkce jsou:

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Ověřuje, že ovládací prvek umožňuje použití v době návrhu, a to tak, že zkontroluje, jestli je v systému přítomnost licenčního souboru ovládacího prvku. Tato funkce je volána rozhraním jako součást zpracování `IClassFactory2::GetLicInfo` a `IClassFactory::CreateInstanceLic`.

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Požaduje jedinečný klíč z knihovny DLL ovládacího prvku. Tento klíč je vložen do aplikace typu kontejner a používá se později v kombinaci s `VerifyLicenseKey`pro vytvoření instance ovládacího prvku. Tato funkce je volána rozhraním jako součást zpracování `IClassFactory2::RequestLicKey`.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Ověřuje, zda jsou vložený klíč a jedinečný klíč ovládacího prvku stejné. Kontejner umožňuje vytvořit instanci ovládacího prvku pro jeho použití. Tato funkce je volána rozhraním jako součást zpracování `IClassFactory2::CreateInstanceLic` a může být přepsána, aby poskytovala přizpůsobené ověření licenčního klíče. Výchozí implementace provede porovnání řetězců. Další informace najdete v části [přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)dále v tomto článku.

###  <a name="_core_header_file_modifications"></a>Úpravy hlavičkových souborů

Průvodce ovládacím prvkem ActiveX umístí do souboru hlaviček ovládacího prvku následující kód. V tomto příkladu jsou deklarovány dvě členské funkce `CSampleCtrl`objektů `factory`, jeden, který ověřuje přítomnost ovládacího prvku. Soubor. LIC a druhý, který načte licenční klíč, který se má použít v aplikaci obsahující tento ovládací prvek:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a>Úpravy souborů implementace

Průvodce ovládacím prvkem ActiveX umístí následující dva příkazy do implementačního souboru ovládacího prvku k deklaraci názvu souboru licence a řetězce licence:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Pokud upravíte `szLicString` jakýmkoli způsobem, je nutné změnit také první řádek v ovládacím prvku. Soubor. LIC nebo licencování nebude fungovat správně.

Průvodce ovládacím prvkem ActiveX umístí do implementačního souboru ovládacího prvku následující kód k definování třídy ovládacího prvku ' `VerifyUserLicense` a `GetLicenseKey` funkce:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Nakonec **Průvodce ovládacím prvkem ActiveX** upraví projekt ovládacího prvku. Soubor IDL Klíčové slovo **licencované** je přidáno do deklarace třídy ovládacího prvku, jak je uvedeno v následujícím příkladu:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a>Přizpůsobení licencování ovládacího prvku ActiveX

Vzhledem k tomu, že `VerifyUserLicense`, `GetLicenseKey`a `VerifyLicenseKey` jsou deklarovány jako virtuální členské funkce třídy Factory ovládacího prvku, lze přizpůsobit chování řízení licencování ovládacího prvku.

Můžete například zadat několik úrovní licencování pro ovládací prvek přepsáním `VerifyUserLicense` nebo `VerifyLicenseKey` členských funkcí. V rámci této funkce můžete upravit, které vlastnosti nebo metody budou uživateli k dispozici v závislosti na úrovni licence, kterou jste zjistili.

Můžete také přidat kód do funkce `VerifyLicenseKey`, která poskytuje přizpůsobenou metodu pro informování uživatele, který vytvoření ovládacího prvku selhalo. Například ve vaší členské funkci `VerifyLicenseKey` můžete zobrazit okno se zprávou oznamující, že se ovládacímu prvku nepodařilo inicializovat a proč.

> [!NOTE]
>  Dalším způsobem přizpůsobení ověření licence ovládacího prvku ActiveX je kontrola registrační databáze pro určitý klíč registru místo volání `AfxVerifyLicFile`. Příklad výchozí implementace najdete v části věnované [úpravám implementačních souborů](#_core_implementation_file_modifications) v tomto článku.

Další diskuzi o problémech s licencováním najdete v části problémy s licencováním v tématu [upgrade existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../mfc/reference/mfc-activex-control-wizard.md)
