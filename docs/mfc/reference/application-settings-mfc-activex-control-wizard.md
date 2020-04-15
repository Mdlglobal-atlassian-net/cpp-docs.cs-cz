---
title: Nastavení aplikace, průvodce ovládacím prvkem ActiveX v prostředí MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.appset
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
ms.openlocfilehash: 55f202ffabe945e55589ab1fc771a1757e23ca2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372480"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Nastavení aplikace, průvodce ovládacím prvkem ActiveX v prostředí MFC

Na této stránce Průvodce ovládacím prvkem ActiveX knihovny MFC můžete navrhnout a přidat základní funkce do nového projektu ActiveX knihovny MFC. Tato nastavení platí pro samotnou aplikaci a nikoli pro žádnou konkrétní funkci nebo prvek ovládacího prvku.

- **Licence za běhu**

   Tuto možnost vyberte, chcete-li vygenerovat uživatelský licenční soubor, který se bude distribuovat s ovládacím prvkem. Licence je textový soubor, *projname*.lic. Tento soubor musí být ve stejném adresáři jako dll ovládacího prvku, aby mohla být vytvořena instance ovládacího prvku v prostředí návrhu. Tento soubor obvykle distribuujete s ovládacím prvkem, ale zákazníci jej nedistribuují.

- **Generovat soubory nápovědy**

   Tuto možnost vyberte, chcete-li generovat soubory nápovědy se zakázaným inzerováním a nakonfigurovat projekt tak, aby zahrnoval nápovědu pro ovládací prvek. Výchozí projekt, vytvořený bez této možnosti, generuje pouze **pole O,** které se zobrazí, když uživatel klepne pravým tlačítkem myši na ovládací prvek, použije klávesu F1 nebo klepne na **nápovědu** v kontejneru ovládacího prvku.

   > [!NOTE]
   > Způsob zobrazení nápovědy závisí na tom, jak ovládací prvek spolupracuje s kontejnerem. Pokud zahrnete pomoc s kontejnerem, je nutné zpracovat zprávy mezi ovládacím prvkem a kontejneru odpovídajícím způsobem zobrazit nápovědu.

   Při generování souborů nápovědy pomocí průvodce obsahuje projekt následující:

  - Soubor .vcxproj obsahuje kód pro sestavení a konfiguraci souboru nápovědy při vytváření projektu.

  - Soubor *projnamePropPage*.cpp obsahuje funkci [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) v konstruktoru.

  - Soubor projname.hpj je soubor projektu nápovědy používaný kompilátorem nápovědy k vytvoření souboru nápovědy ovládacího prvku ActiveX. Soubor HPJ je textový soubor obsahující informace o vytváření souboru nápovědy a cesty k dalším souborům (například k bitmapám), které soubor nápovědy obsahuje.

  - Projekt obsahuje adresář HLP, který obsahuje bitmapové soubory nápovědy projektu a soubor tématu*nápovědy (projname*.rtf). Tento soubor tématu nápovědy obsahuje standardní témata nápovědy pro běžné vlastnosti, události a metody podporované mnoha ovládacími prvky ActiveX. Soubor RTF můžete upravit a přidat nebo odebrat určitá témata nápovědy.

## <a name="see-also"></a>Viz také

[Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)<br/>
[Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)
