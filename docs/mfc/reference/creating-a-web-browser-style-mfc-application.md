---
title: Vytváření aplikací MFC ve stylu webového prohlížeče
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: 9d249c7effc2c78e319207d82c9a963d7a61a67c
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504765"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Vytváření aplikací MFC ve stylu webového prohlížeče

Webovou aplikaci ve stylu prohlížeče můžete přístup k informacím z Internetu (například HTML nebo aktivní dokumenty) nebo intranet, stejně jako složky v místním systému souborů a v síti. Odvozené třídy zobrazení vaší aplikace z [CHtmlView](../../mfc/reference/chtmlview-class.md), efektivně provedete webový prohlížeč pro aplikaci tím, že poskytuje zobrazení pomocí ovládacího prvku WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>K vytvoření webové aplikace v prohlížeči podle architektury dokument/zobrazení MFC

1. Postupujte podle pokynů v [vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md).

1. V Průvodce aplikací MFC [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránce, provedení určitých, který **architekturu Document/view** je zaškrtnuté políčko. (Můžete zvolit **jednotlivý dokument** nebo **více dokumentů**, ale ne **na bázi dialogu**.)

1. Na [třídy generované v revizi](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky, použijte **základní třída** rozevírací nabídky vyberte `CHtmlView`.

1. Vyberte další možnosti, které chcete, aby integrované do kostry aplikace.

1. Klikněte na tlačítko **Dokončit**.

Ovládací prvek WebBrowser podporuje, procházení webu pomocí hypertextové odkazy a navigace Uniform Resource Locator (URL). Ovládací prvek udržuje seznam historie, který umožňuje uživateli procházet vpřed a zpět mezi předchozích navštívených stránek lokalit, složky a dokumenty. Ovládací prvek přímo zpracovává navigační, hypertextové odkazy, seznamy historie, Oblíbené položky a zabezpečení. Aplikace slouží jako kontejner pro aktivní dokument pro hostování aktivního dokumentu ovládací prvek WebBrowser. Proto bohatě formátovaná dokumenty, jako jsou tabulky Microsoft Excel nebo dokumentů aplikace Word lze otevřít a upravit v rámci ovládacího prvku WebBrowser. WebBrowser – ovládací prvek je také kontejnerem ovládacího prvku ActiveX, který může hostovat jakýkoli ovládací prvek ActiveX.

> [!NOTE]
>  Ovládací prvek WebBrowser ActiveX (a tedy `CHtmlView`) je dostupná jenom pro aplikace běžící v rámci verze Windows, ve které aplikace Internet Explorer 4.0 nebo novější bylo nainstalováno.

Protože `CHtmlView` jednoduše implementuje ovládací prvek webu prohlížeče, podporu pro tisk není jako jiné [CView](../../mfc/reference/cview-class.md)-odvozené třídy. Místo toho ovládací prvek WebBrowser implementuje v uživatelském rozhraní tiskárny a tisku. V důsledku toho `CHtmlView` nemá nepodporuje náhled tisku a neposkytuje rozhraní pro další tisk funkce podpory: například [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), a [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), které jsou k dispozici v jiných aplikacích MFC.

`CHtmlView` funguje jako obálka pro ovládací prvek webového prohlížeče, která poskytuje zobrazení na webu nebo stránku HTML vaší aplikace. Průvodce vytvoří, přepíše [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) funkce ve třídě zobrazení poskytující navigační odkaz na web Microsoft Visual C++:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

Tento web můžete nahradit vlastním, nebo můžete použít [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) členské funkce a otevřete stránku HTML, který se nachází v skript prostředků projektu jako výchozí obsah pro zobrazení. Příklad:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MFCIE](https://github.com/Microsoft/VCSamples)<br/>
[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)<br/>
[Nastavení kompilátoru a vlastnosti sestavení](../../build/working-with-project-properties.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)<br/>
[Nastavení kompilátoru a vlastnosti sestavení](../../build/working-with-project-properties.md)

