---
title: 'MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX'
ms.date: 11/19/2018
f1_keywords:
- COleObjectFactory
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: 35ca5d410f642f2557d9ee797eda2d9529f7f4d1
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176354"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX

Licencování podpory, volitelná funkce ovládacích prvků ActiveX, vám umožní řídit, kdo může pro používání nebo distribuci ovládacího prvku. (Další informace o licencování problémy, podívejte se na licencování problémy v [upgrade existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Tento článek popisuje v následujících tématech:

- [Přehled licencování ovládacího prvku ActiveX](#_core_overview_of_activex_control_licensing)

- [Vytváření licencovaného ovládacího prvku](#_core_creating_a_licensed_control)

- [Licencování podpory](#_core_licensing_support)

- [Přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Ovládací prvky ActiveX, které implementují licencování, povolit jako vývojář ovládacího prvku, chcete-li zjistit, jak jiní lidé budou pomocí ovládacího prvku ActiveX. Zadejte nakupující ovládacího prvku pomocí ovládacího prvku a. Soubor – licenční smlouva s smlouvě, že nabyvatel může distribuovat ovládacího prvku, ale ne. Soubor – licenční smlouva s aplikaci používající ovládací prvek. To zabrání uživatelům této aplikace z psaní nové aplikace, které pomocí ovládacího prvku, bez první ovládací prvek od vás licencování.

##  <a name="_core_overview_of_activex_control_licensing"></a> Přehled licencování ovládacího prvku ActiveX

Kvůli zajištění podpory správy licencí pro ovládací prvky ActiveX, [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) třída poskytuje implementaci pro několik funkcí v `IClassFactory2` rozhraní: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, a `IClassFactory2::CreateInstanceLic`. Když vývojář aplikace kontejneru vytváří požadavek na vytvoření instance ovládacího prvku, volání `GetLicInfo` se provádí pro ověření, že ovládací prvek. Soubor – licenční smlouva je k dispozici. Pokud je licencován ovládacího prvku, lze vytvořit a umístí do kontejneru instance ovládacího prvku. Po dokončení vytváření aplikace typu kontejner vývojář jinou funkci volání, tentokrát s `RequestLicKey`, je proveden. Tato funkce vrací licenční klíč (řetězec jednoduchého znaků) pro aplikace typu kontejner. Vrácené klíč bude poté vložen v aplikaci.

Obrázek níže ukazuje ověřování licencí ovládacího prvku ActiveX, který se použije při vývoji aplikace typu kontejner. Jak už bylo zmíněno dříve, vývojář aplikace kontejneru musí mít správné. Soubor – licenční smlouva nainstalována na vývojovém počítači k vytvoření instance ovládacího prvku.

![Licencované ovládací prvek ActiveX ověřit na vývoj](../mfc/media/vc374d1.gif "ovládacího prvku ActiveX licenci ověřit na vývoj") <br/>
Ověření licencovaného ovládacího prvku ActiveX během vývoje.

Další proces je znázorněno na následujícím obrázku, nastane, když koncový uživatel spustí aplikace typu kontejner.

Při spuštění aplikace obvykle potřeba vytvořit instanci ovládacího prvku. Kontejner toho dosahuje tím, že zavoláte na `CreateInstanceLic`, předá vložený licenční klíč jako parametr. Porovnání řetězců se pak mezi vložený licenční klíč a ovládacího prvku vlastní kopii licenční klíč. Pokud tato shoda je úspěšná, je vytvořena instance ovládacího prvku a aplikace pokračuje v provádění normálně. Všimněte si, že. Soubor – licenční smlouva nemusí být k dispozici v počítači uživatele ovládacího prvku.

![Licencované ovládací prvek ActiveX ověřit při spuštění](../mfc/media/vc374d2.gif "ovládacího prvku ActiveX licenci ověřit při spuštění") <br/>
Ověření licencovaného ovládacího prvku ActiveX během provádění

Licencování ovládacích prvků se skládá ze dvou částí: základní: konkrétního kódu v implementaci ovládacího prvku knihovny DLL a soubor s licencí. Kód se skládá z dvou (nebo případně tří) volání funkcí a řetězec znaků, dále jen "licence řetězec", obsahující o autorských právech. Tato volání a řetězec licence se nacházejí v implementaci ovládacího prvku (. Soubor CPP). Soubor licence, generované průvodcem ovládací prvek ActiveX, je textový soubor s prohlášení o autorských právech. Má název, název projektu s využitím. Rozšíření – licenční smlouva, například vzorek. – LICENČNÍ SMLOUVA. Licencovaný ovládací prvek musí být doplněny licenční soubor, v případě potřeby použijte návrhu.

##  <a name="_core_creating_a_licensed_control"></a> Vytváření licencovaného ovládacího prvku

Když použijete Průvodce ovládacím prvkem ActiveX k vytvoření rozhraní ovládacího prvku, je snadné obsahují licenci podpory. Pokud určíte, že ovládací prvek by měl mít licenci za běhu, Průvodce ovládacím prvkem ActiveX kód přidá do třídy ovládacího prvku pro podporu licencování. Kód se skládá z funkcí, které používají soubor klíče a licence pro ověřování licencí. Tyto funkce lze také upravit a přizpůsobit licencování ovládacích prvků. Další informace o přizpůsobení licenci, najdete v části [přizpůsobení Licensing ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control) dále v tomto článku.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Přidání podpory pro licence pomocí Průvodce ovládacím prvkem ActiveX při vytvoření projektu ovládacího prvku

1. Postupujte podle pokynů v [vytvoření ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md). **Nastavení aplikace** stránky Průvodce ovládacím prvkem ActiveX obsahuje možnost vytvoření ovládacího prvku s licencí za běhu.

Průvodce ovládacím prvkem ActiveX nyní generuje rozhraní ovládacího prvku ActiveX, který obsahuje základní licencování podpory. Podrobné vysvětlení licenční kód najdete v dalším tématu.

##  <a name="_core_licensing_support"></a> Licencování podpory

Při použití Průvodce ovládacím prvkem ActiveX pro přidání do ovládacího prvku ActiveX licencování podpory, Průvodce ovládacím prvkem ActiveX přidá kód, který deklaruje a implementuje licencování funkci se přidá do ovládacího prvku záhlaví a implementace soubory. Tento kód se skládá z `VerifyUserLicense` členské funkce a `GetLicenseKey` členskou funkci, která přepsat výchozí implementace v [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Tyto funkce načíst a ověření licence ovládacího prvku.

> [!NOTE]
>  Třetí členská funkce `VerifyLicenseKey` pomocí Průvodce ovládacím prvkem ActiveX, ale může být potlačena za účelem přizpůsobení chování klíče ověření licence.

Tyto členské funkce jsou:

- [Verifyuserlicense –](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Ověřuje, že ovládací prvek umožňuje využití návrhu kontrolou systému přítomnost licenční soubor ovládacího prvku. Tato funkce se volá se rozhraním při zpracování `IClassFactory2::GetLicInfo` a `IClassFactory::CreateInstanceLic`.

- [Getlicensekey –](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Požádá o jedinečný klíč z ovládacího prvku knihovny DLL. Tento klíč je součástí aplikace typu kontejner a později, použít ve spojení s `VerifyLicenseKey`, chcete-li vytvořit instanci ovládacího prvku. Tato funkce se volá se rozhraním při zpracování `IClassFactory2::RequestLicKey`.

- [Verifylicensekey –](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Ověří, zda vložený klíč a jedinečný klíč ovládacího prvku jsou stejné. To umožňuje kontejneru pro vytvoření instance ovládacího prvku pro jeho použití. Tato funkce se volá se rozhraním při zpracování `IClassFactory2::CreateInstanceLic` a může být potlačena za účelem poskytovat vlastní ověření licenční klíč. Výchozí implementace provádí porovnání řetězců. Další informace najdete v tématu [přizpůsobení Licensing ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)dále v tomto článku.

###  <a name="_core_header_file_modifications"></a> Úpravy souborů záhlaví

Průvodce ovládacím prvkem ActiveX umístí následující kód do souboru záhlaví ovládacího prvku. V tomto příkladu dvě členské funkce `CSampleCtrl`uživatele objektu `factory` jsou deklarovány, ten, který se ověřuje přítomnost ovládacího prvku. Soubor – licenční smlouva a další vlastnost, která načte licenční klíč, který se má použít v aplikaci obsahující ovládací prvek:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a> Implementace úpravy souborů

Průvodce ovládacím prvkem ActiveX umístí následující dva příkazy v souboru implementace ovládacího prvku pro deklaraci licence řetězec a název souboru licencí:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Pokud upravíte `szLicString` žádným způsobem, je také nutné upravit první řádek v ovládacím prvku. Soubor – licenční smlouva nebo licencí nebude fungovat správně.

Průvodce ovládacím prvkem ActiveX umístí následující kód v souboru implementace ovládacího prvku pro definování ovládacího prvku třídy `VerifyUserLicense` a `GetLicenseKey` funkce:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Nakonec **Průvodce ovládacím prvkem ActiveX** změní projekt, na ovládací prvek. Soubor IDL. **Licenci** – klíčové slovo je přidán do deklarace coclass ovládacího prvku, jako v následujícím příkladu:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Přizpůsobení licencování ovládacího prvku ActiveX

Protože `VerifyUserLicense`, `GetLicenseKey`, a `VerifyLicenseKey` jsou deklarovány jako virtuální členské funkce třídy objekt pro vytváření ovládacího prvku můžete přizpůsobit chování licencování ovládacího prvku.

Například můžete zadat několik úrovní licencování pro ovládací prvek tak, že přepíšete `VerifyUserLicense` nebo `VerifyLicenseKey` členské funkce. V této funkci může upravit, které vlastnosti nebo metody jsou vystaveny pro uživatele podle úrovně licenci se zjištěným.

Můžete také přidat kód, který `VerifyLicenseKey` funkce, která poskytuje vlastní metodu pro informování uživatele, který řídí vytvoření se nezdařilo. Například ve vašich `VerifyLicenseKey` pole členská funkce může zobrazit zpráva oznamující, že ovládací prvek se nezdařila a proč.

> [!NOTE]
>  Jinou možností přizpůsobení ověřování licencí ovládacího prvku ActiveX je kontrola registrační databázi pro klíč registru, namísto volání metody `AfxVerifyLicFile`. Příklad výchozí implementaci, najdete v článku [úpravy souborů implementace](#_core_implementation_file_modifications) části tohoto článku.

Další informace o licencování problémy, podívejte se na licencování problémy v [upgrade existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../mfc/reference/mfc-activex-control-wizard.md)

