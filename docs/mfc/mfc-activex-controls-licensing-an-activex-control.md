---
title: 'Ovládací prvky MFC ActiveX: Licencování ovládacích prvků ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 725e6cf167ec01635a3072f09ecaa2f5055b1891
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX
Licencování podpory, volitelná funkce ovládacích prvků ActiveX, můžete určit, kdo může použít nebo distribuovat ovládacího prvku. (Další informace o licenčních podmínkách, najdete v části licencování problémy v [upgradování existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).)  
  
 Tento článek popisuje v následujících tématech:  
  
-   [Přehled ovládacích prvků ActiveX pro licencování](#_core_overview_of_activex_control_licensing)  
  
-   [Vytvoření ovládacího prvku licencovanou](#_core_creating_a_licensed_control)  
  
-   [Licencování podpory](#_core_licensing_support)  
  
-   [Přizpůsobení licencování ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)  
  
 Ovládací prvky ActiveX, které implementovat licencování, povolit jako vývojář ovládacího prvku, chcete-li zjistit, jak jiní lidé bude používat ovládací prvek ActiveX. Zadejte nakupující ovládacího prvku pomocí ovládacího prvku a. Soubor – licenční smlouva s smlouvu, kupující může distribuci ovládacího prvku, ale ne. Soubor – licenční smlouva s aplikaci, která používá ovládacího prvku. To zabrání uživatelům této aplikace z zápis nové aplikace, které používají řízení, bez první licencování ovládacího prvku od vás.  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> Přehled ovládacích prvků ActiveX pro licencování  
 K podpoře licencování pro ovládací prvky ActiveX, [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) třída poskytuje implementaci pro několik funkcí v **IClassFactory2** rozhraní: **IClassFactory2 :: RequestLicKey**, **IClassFactory2::GetLicInfo**, a **IClassFactory2::CreateInstanceLic**. Když vývojář aplikace kontejneru vytváří požadavek na vytvoření instance ovládacího prvku, volání `GetLicInfo` Přišla žádost o ověřte, že ovládací prvek. Soubor – licenční smlouva není k dispozici. Pokud ovládací prvek je licencována, instanci ovládacího prvku můžete vytvořit a umístěna v kontejneru. Po dokončení vytváření aplikací kontejneru vývojář jinou funkci volat, tentokrát s `RequestLicKey`, se provádí. Tato funkce vrátí do kontejnerové aplikace licenční klíč (řetězec jednoduchého znaků). Vrácený klíč je pak vloženy do aplikace.  
  
 Následující obrázek ukazuje ověření licencí ovládacího prvku ActiveX, který se použije během vývoje aplikace kontejneru. Jak je uvedeno nahoře, musí mít vývojář aplikace kontejneru správné. Soubor – licenční smlouva nainstalovaný na vývojovém počítači k vytvoření instance ovládacího prvku.  
  
 ![Licencované ovládací prvek ActiveX ověřit na vývoj](../mfc/media/vc374d1.gif "vc374d1")  
Ověření licencované ovládací prvek ActiveX během vývoje  
  
 Další proces vidět na následujícím obrázku, nastane, když koncový uživatel spustí aplikaci kontejneru.  
  
 Když se aplikace spustí, obvykle nutné vytvořit instanci ovládacího prvku. Kontejner toho dosahuje tím, že zavoláte na `CreateInstanceLic`, předávání embedded licenční klíč jako parametr. Porovnání řetězců se pak mezi embedded licenční klíč a ovládacího prvku vlastní kopii licenční klíč. Pokud shody je úspěšné, je vytvořena instance ovládacího prvku a aplikace bude pokračovat v provádění normálně. Všimněte si, že. Na počítači uživatele řízení nemusí být soubor – licenční smlouva.  
  
 ![Licencované ovládací prvek ActiveX ověřit v provádění](../mfc/media/vc374d2.gif "vc374d2")  
Ověření licencované ovládací prvek ActiveX během provádění  
  
 Licencování ovládacích obsahuje dvě základní součásti: konkrétní kód v implementaci ovládacího prvku knihovna DLL a soubor licencí. Kód se skládá z volání funkce dva (nebo případně tří) a řetězec znaků, dále jen "licenční řetězec", obsahující autorských právech. Řetězec licence a těchto volání, které se nacházejí v implementaci ovládacího prvku (. Soubor CPP). Soubor licencí generované průvodcem ovládací prvek ActiveX, je textový soubor s prohlášení o autorských právech. Pomocí názvu projektu s je název. Rozšíření – licenční smlouva, například ukázka. – LICENČNÍ SMLOUVA. Licencované ovládací prvek musí být doplněn licenční soubor je podle potřeby použijte návrhu.  
  
##  <a name="_core_creating_a_licensed_control"></a> Vytvoření ovládacího prvku licencovanou  
 Pokud použijete Průvodce ovládacím prvkem ActiveX k vytvoření rozhraní ovládací prvek, je snadné zahrnují licencování podpory. Pokud určíte, že ovládacího prvku by měl mít licenci běhu, Průvodce ovládacím prvkem ActiveX přidá kód na ovládací prvek třídy pro podporu licencování. Kód obsahuje funkce, které použít pro ověření licenční soubor klíče a licence. Tyto funkce můžete také upravit tak, aby přizpůsobení ovládacího prvku licencování. Další informace o přizpůsobení licencí najdete v tématu [přizpůsobení Licensing ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control) dále v tomto článku.  
  
#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Chcete-li přidat podporu pro licencování s Průvodce ovládacím prvkem ActiveX při vytváření projektu ovládací prvek  
  
1.  Postupujte podle pokynů v [vytvoření ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md). **Nastavení aplikace** stránky Průvodce ovládacím prvkem ActiveX obsahuje možnost vytvoření ovládacího prvku s licencí běhu.  
  
 Průvodce ovládacím prvkem ActiveX nyní generuje představuje rozhraní pro ovládací prvek ActiveX, které zahrnuje podporu základní licencování. Podrobné vysvětlení licenční kód naleznete v tématu Další.  
  
##  <a name="_core_licensing_support"></a> Licencování podpory  
 Pokud použijete Průvodce ovládacím prvkem ActiveX přidání licencování podpory do ovládacího prvku ActiveX, Průvodce ovládacím prvkem ActiveX přidá kód, který deklaruje a implementuje licencování schopnosti je přidán do ovládacího prvku záhlaví a implementace soubory. Tento kód se skládá z `VerifyUserLicense` – členská funkce a `GetLicenseKey` členská funkce, které potlačí výchozí implementace najít v [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Tyto funkce načíst a ověření licence na ovládací prvek.  
  
> [!NOTE]
>  Třetí členská funkce `VerifyLicenseKey` není generované průvodcem ovládací prvek ActiveX, ale může být potlačena za účelem přizpůsobení chování ověření klíče licence.  
  
 Tyto členské funkce jsou:  
  
-   [Verifyuserlicense –](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)  
  
     Ověřuje, že ovládací prvek umožňuje využití návrhu kontrolou systému přítomnost souboru s licencí ovládacího prvku. Tato funkce je volána rozhraním framework jako součást zpracování **IClassFactory2::GetLicInfo** a **IClassFactory::CreateInstanceLic**.  
  
-   [Getlicensekey –](../mfc/reference/coleobjectfactory-class.md#getlicensekey)  
  
     Jedinečný klíč požadavků z ovládacího prvku knihovny DLL. Tento klíč je vloženy do kontejneru aplikace a později, používá ve spojení s `VerifyLicenseKey`, k vytvoření instance ovládacího prvku. Tato funkce je volána rozhraním framework jako součást zpracování **IClassFactory2::RequestLicKey**.  
  
-   [Verifylicensekey –](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)  
  
     Ověřuje, že embedded klíč a jedinečný klíč ovládacího prvku jsou stejné. To umožňuje kontejneru pro vytvoření instance ovládacího prvku pro jeho použití. Tato funkce je volána rozhraním framework jako součást zpracování **IClassFactory2::CreateInstanceLic** a může být potlačena za účelem poskytovat přizpůsobené ověření licenční klíč. Výchozí implementace provede porovnání řetězců. Další informace najdete v tématu [přizpůsobení Licensing ovládacího prvku ActiveX](#_core_customizing_the_licensing_of_an_activex_control)dál v tomto článku.  
  
###  <a name="_core_header_file_modifications"></a> Úpravy soubor hlaviček  
 Průvodce ovládacím prvkem ActiveX umístí následující kód do ovládacího prvku záhlaví souboru. V tomto příkladu dva členské funkce `CSampleCtrl`je objekt `factory` jsou deklarovány, ten, který ověří přítomnost ovládacího prvku. Soubor – licenční smlouva a druhý, který načte licenční klíč, který se má použít v aplikaci obsahující ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> Implementace úpravy souborů  
 Průvodce ovládacím prvkem ActiveX umístí následující dva příkazy v řídicím souboru implementace deklarovat název souboru licencí a licencí řetězec:  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  Pokud změníte **szLicString** žádným způsobem, musíte také upravit první řádek v ovládacím prvku. Soubor – licenční smlouva nebo licencování nebude fungovat správně.  
  
 Průvodce ovládacím prvkem ActiveX umístí následující kód do souboru implementaci ovládacího prvku k definování ovládacího prvku třídy `VerifyUserLicense` a `GetLicenseKey` funkce:  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 Nakonec **Průvodce ovládacím prvkem ActiveX** upraví řízení projektu. IDL soubor. **Licenci** – klíčové slovo se přidá do deklaraci třída typu coclass ovládacího prvku, jako v následujícím příkladu:  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Přizpůsobení licencování ovládacího prvku ActiveX  
 Protože `VerifyUserLicense`, `GetLicenseKey`, a `VerifyLicenseKey` jsou deklarovány jako virtuální členské funkce ovládacího prvku objekt pro vytváření třídy, můžete přizpůsobit chování licencování ovládacího prvku.  
  
 Například můžete zadat několik úrovní licencování pro ovládací prvek přepsáním `VerifyUserLicense` nebo `VerifyLicenseKey` členské funkce. Uvnitř této funkce může upravit, které vlastnosti nebo metody jsou viditelné na uživatele podle úrovně licencí, které jste rozpoznali.  
  
 Můžete také přidat kód pro `VerifyLicenseKey` funkce, která poskytuje vlastní metodu pro informující uživatele, který řídí vytváření se nezdařilo. Například ve vaší `VerifyLicenseKey` pole – členská funkce může zobrazí zpráva oznamující, že ovládacího prvku se nepodařilo inicializovat a proč.  
  
> [!NOTE]
>  Jiný způsob, jak přizpůsobit ověření licencí ovládacího prvku ActiveX je zkontrolujte registraci databáze pro konkrétní klíč, namísto volání `AfxVerifyLicFile`. Příklad výchozí implementaci, najdete v článku [úpravy souborů implementace](#_core_implementation_file_modifications) tohoto článku.  
  
 Další informace o licenčních podmínkách, najdete v části licencování problémy v [upgradování existujícího ovládacího prvku ActiveX](../mfc/upgrading-an-existing-activex-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Průvodce ovládacím prvkem ActiveX v prostředí MFC](../mfc/reference/mfc-activex-control-wizard.md)

