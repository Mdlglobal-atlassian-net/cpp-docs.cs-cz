---
title: 'TN071: MFC iolecommandtarget – implementace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d8d4b0f740e69b57944cb35f2213ae0fd54b511
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386285"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: MFC IOleCommandTarget – implementace

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

`IOleCommandTarget` Rozhraní umožňuje objektů a jejich kontejnerů k odeslání příkazů k sobě navzájem. Například objektu panely nástrojů mohou obsahovat tlačítka pro příkazy, jako `Print`, `Print Preview`, `Save`, `New`, a `Zoom`. Pokud takový objekt byly vloženy do kontejneru, který podporuje `IOleCommandTarget`, objekt může povolit jeho tlačítka a předávání příkazy na kontejner zpracováním, když uživatel klikl na ně. Pokud kontejner vloženého objektu, aby se vytiskl, ho můžete provést tuto žádost o odeslání příkazu prostřednictvím `IOleCommandTarget` rozhraní vloženého objektu.

`IOleCommandTarget` Automatizace jako rozhraní je v tom, že se používá pro klienta k vyvolání metody na serveru. Avšak použití `IOleCommandTarget` šetří režii volání prostřednictvím rozhraní automatizace protože programátoři nemusíte používat obvykle nákladné `Invoke` metoda `IDispatch`.

V knihovně MFC `IOleCommandTarget` rozhraní používá servery pro aktivní dokumenty umožňující kontejnery pro aktivní dokument k odeslání příkazů na server. Třída serveru aktivního dokumentu, `CDocObjectServerItem`, používá mapy rozhraní MFC (naleznete v tématu [TN038: MFC/OLE – implementace třídy IUnknown](../mfc/tn038-mfc-ole-iunknown-implementation.md)) k implementaci `IOleCommandTarget` rozhraní.

`IOleCommandTarget` také je implementována `COleFrameHook` třídy. `COleFrameHook` je nedokumentované třídy knihovny MFC, která implementuje funkce okna rámce kontejnerů úpravy na místě. `COleFrameHook` mapy rozhraní MFC používá také k implementaci `IOleCommandTarget` rozhraní. `COleFrameHook`pro implementaci `IOleCommandTarget` předává příkazy OLE, které `COleDocObjectItem`-odvozené kontejnery pro aktivní dokument. To umožňuje libovolné MFC aktivní kontejner dokumentu pro příjem zpráv z servery pro aktivní dokumenty obsažené.

## <a name="mfc-ole-command-maps"></a>Mapy příkazů MFC OLE

MFC vývojáři můžou využít výhod `IOleCommandTarget` pomocí knihovny MFC OLE příkazu mapy. Mapy příkazů OLE jsou jako mapy zpráv, protože slouží k mapování příkazy OLE na členské funkce třídy, která obsahuje mapu příkazu. Chcete-li tuto práci, umístěte na mapě příkaz k určení příkazu skupiny OLE požadovaný příkaz, příkaz OLE a Identifikátor příkazu makra [wm_command –](/windows/desktop/menurc/wm-command) zprávu, která se pošle při přijetí příkazu technologie OLE. Knihovna MFC také poskytuje řadu předdefinovaných maker pro standardní příkazy OLE. Seznam standardní technologie OLE příkazy, které byly původně určena pro použití s aplikací Microsoft Office naleznete v tématu OLECMDID výčet, který je definován v docobj.h.

Po přijetí příkazu technologie OLE aplikací MFC, která obsahuje mapu příkaz OLE MFC se pokusí najít ID příkazu a skupinu příkazů pro požadovaný příkaz v objektu map OLE příkazu aplikace. Pokud se najde shoda, je odeslána aplikace obsahující příkaz mapy s ID požadovaný příkaz wm_command – zprávy. (Viz popis `ON_OLECMD` níže.) Tímto způsobem jsou odeslána do aplikace příkazy OLE převedena na wm_command – zprávy v prostředí MFC. Wm_command – zprávy jsou pak směrován přes mapy zpráv aplikace pomocí knihovny MFC standardu [směrování příkazů](../mfc/command-routing.md) architektury.

Na rozdíl od mapy zpráv mapy příkazů MFC OLE nejsou podporována nástrojem ClassWizard. MFC musí vývojáři přidat podporu mapování příkazů OLE a položek OLE příkaz mapování ručně. Příkaz OLE mapy mohou být přidány do knihovny MFC aktivní servery dokumentu do třídy, která je v řetězu wm_command – směrování zpráv v době aktivní dokument je na místě aktivní v kontejneru. Tyto třídy zahrnují aplikace třídy odvozené od [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), a [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). V kontejnery pro aktivní dokument, mapy příkazů OLE lze přidat pouze k [coledocobjectitem –](../mfc/reference/coledocobjectitem-class.md)-odvozené třídy. Také v kontejnery pro aktivní dokument, wm_command – zprávy pouze odeslán do mapy zpráv v `COleDocObjectItem`-odvozené třídy.

## <a name="ole-command-map-macros"></a>Makra Map příkaz OLE

Chcete-li přidat příkaz mapování funkce do vaší třídy, použijte následující makra:

```cpp
DECLARE_OLECMD_MAP ()
```

Toto makro přejde v deklaraci třídy (obvykle v souboru hlaviček) třídy, která obsahuje mapu příkazu.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
Název třídy, která obsahuje mapu příkazu.

*baseClass*<br/>
Název třídy základní třídy, která obsahuje mapu příkazu.

Toto makro označuje začátek toho příkaz mapy. Použijte toto makro v souboru implementace pro třídu, která obsahuje mapu příkazu.

```
END_OLECMD_MAP()
```

Toto makro označuje konec příkazu mapy. Použijte toto makro v souboru implementace pro třídu, která obsahuje mapu příkazu. Toto makro musí vždycky dodržovat BEGIN_OLECMD_MAP – makro.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Ukazatel na identifikátor GUID skupiny příkazů příkaz OLE. Tento parametr je **NULL** pro skupiny standardních příkazů OLE.

*olecmdid*<br/>
ID příkazu OLE příkazu má být volána.

*id*<br/>
ID wm_command – zprávy k odeslání do aplikace obsahující mapování příkazu, když uživatel vyvolá příkaz OLE.

Použíjte ON_OLECMD – makro v mapě příkaz mohli přidat záznamy pro příkazy OLE, které chcete zpracovávat. Po přijetí jsou příkazy OLE, bude se převést na zadaný wm_command – zprávy a směrován přes mapu zpráv aplikace pomocí standardního směrování příkazů architektury MFC.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat schopnost OLE zpracování příkazu služby MFC Active document server ke zpracování [OLECMDID_PRINT](/windows/desktop/api/docobj/ne-docobj-olecmdid) příkaz OLE. Tento příklad předpokládá, že jste použili k vygenerování aplikace knihovny MFC, která je server aktivní dokument AppWizard.

1. Ve vaší `CView`– odvozené třídy záhlaví souboru, přidá dané makro DECLARE_OLECMD_MAP do deklarace třídy.

    > [!NOTE]
    > Použití `CView`-odvozené třídy, protože je jednou ze tříd v aktivním dokumentu serveru, který je v řetězu wm_command – směrování zpráv.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. V souboru implementace pro `CView`-odvozené třídy, přidejte BEGIN_OLECMD_MAP a END_OLECMD_MAP makra:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Chcete-li zpracovat standardní příkaz pro tisk OLE, přidejte [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) – makro mapování příkazu identifikátorem příkazu OLE pro standardní příkaz pro tisk a **ID_FILE_PRINT** ID. wm_command – **ID_FILE_PRINT** je standardně používané ID příkazu pro tiskové aplikace vygenerované průvodcem MFC:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Všimněte si, že jeden standardní příkaz makra OLE definovaná v afxdocob.h, může být zastoupen ON_OLECMD – makro protože **OLECMDID_PRINT** je standardní OLE ID příkazu. ON_OLECMD_PRINT – makro se provedení stejné úlohy jako ON_OLECMD – makro uvedené výše.

Když aplikace typu kontejner pro odešle tento server **OLECMDID_PRINT** příkaz prostřednictvím serveru `IOleCommandTarget` rozhraní MFC tisk obslužná rutina příkazu, který bude vyvolán na serveru, způsobuje server k vytištění aplikace. Kontejner pro aktivní dokument kódu k vyvolání příkazu print přidali v předchozích krocích by vypadat přibližně takto:

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
