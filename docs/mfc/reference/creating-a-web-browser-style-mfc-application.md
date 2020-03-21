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
ms.openlocfilehash: d928d8de34c6caab0f86e9205d0aea45b5ed737c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079451"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Vytváření aplikací MFC ve stylu webového prohlížeče

Aplikace ve stylu webového prohlížeče má přístup k informacím z Internetu (například HTML nebo Active Documents) nebo intranetu a také ke složkám v místním systému souborů a v síti. Vyvoláním třídy zobrazení aplikace z [CHtmlView –](../../mfc/reference/chtmlview-class.md)efektivně aplikace zpřístupní webový prohlížeč tím, že poskytuje zobrazení s ovládacím prvkem WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Vytvoření aplikace webového prohlížeče na základě architektury document/view knihovny MFC

1. Postupujte podle pokynů v části [Vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Na stránce [Typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) Průvodce aplikací knihovny MFC zaškrtněte políčko **dokument/zobrazení architektury** . (Můžete zvolit buď **jeden dokument** , nebo **více dokumentů**, ale **dialogové okno není založené**.)

1. Na stránce [Kontrola vygenerovaných tříd](../../mfc/reference/generated-classes-mfc-application-wizard.md) použijte rozevírací nabídku **základní třída** k výběru `CHtmlView`.

1. Vyberte další možnosti, které chcete integrovat do kostry aplikace.

1. Klikněte na **Finish** (Dokončit).

Ovládací prvek WebBrowser podporuje procházení webu prostřednictvím odkazů a navigace v rámci adresy URL (Uniform Resource Locator). Ovládací prvek udržuje seznam historie, který uživateli umožňuje procházet předchozí prohlížené weby, složky a dokumenty a procházet je směrem dopředu. Ovládací prvek přímo zpracovává navigaci, hypertextové odkazy, seznamy historie, oblíbené položky a zabezpečení. Aplikace mohou používat ovládací prvek WebBrowser jako kontejner aktivních dokumentů pro hostování aktivních dokumentů. Bohatě formátované dokumenty, například tabulky aplikace Microsoft Excel nebo dokumenty aplikace Word, lze proto otevřít a upravit přímo v ovládacím prvku WebBrowser. Ovládací prvek WebBrowser je také kontejner ovládacího prvku ActiveX, který může hostovat jakýkoli ovládací prvek ActiveX.

> [!NOTE]
>  Ovládací prvek ActiveX WebBrowser (a proto `CHtmlView`) je k dispozici pouze pro aplikace, které jsou spuštěny ve verzích systému Windows, ve kterých je nainstalována aplikace Internet Explorer 4,0 nebo novější.

Vzhledem k tomu, že `CHtmlView` jednoduše implementuje ovládací prvek webového prohlížeče společnosti Microsoft, podpora pro tisk se nepodobá jiným třídám odvozeným od programu [CView](../../mfc/reference/cview-class.md). Místo toho ovládací prvek WebBrowser implementuje uživatelské rozhraní tiskárny a tisk. V důsledku toho `CHtmlView` nepodporuje náhled tisku a rozhraní neposkytuje pro další funkce podpory tisku: například [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)a [CView:: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), které jsou k dispozici v jiných aplikacích knihovny MFC.

`CHtmlView` slouží jako obálka ovládacího prvku webového prohlížeče, který umožňuje zobrazení vaší aplikace na webu nebo na stránce HTML. Průvodce vytvoří přepsání funkce [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) ve třídě zobrazení a poskytne navigační odkaz na web Microsoft Visual C++ web:

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

Tuto lokalitu můžete nahradit vlastními, nebo můžete pomocí členské funkce [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) otevřít stránku HTML, která se nachází v skriptu prostředků projektu jako výchozí obsah pro zobrazení. Příklad:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Viz také

[MFCIE Sample MFC](https://github.com/Microsoft/VCSamples)<br/>
[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)<br/>
[Nastavení vlastností kompilátoru a sestavení](../../build/working-with-project-properties.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)<br/>
[Nastavení vlastností kompilátoru a sestavení](../../build/working-with-project-properties.md)
