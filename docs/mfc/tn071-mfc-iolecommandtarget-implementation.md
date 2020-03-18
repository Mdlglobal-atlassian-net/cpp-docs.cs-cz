---
title: 'TN071: MFC IOleCommandTarget – implementace'
ms.date: 06/28/2018
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 56745e7985c8af97b0b628d148586ccef346d95a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442068"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: MFC IOleCommandTarget – implementace

> [!NOTE]
> Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

Rozhraní `IOleCommandTarget` umožňuje objektům a jejich kontejnerům odesílat příkazy do sebe navzájem. Například panely nástrojů objektu mohou obsahovat tlačítka pro příkazy, například `Print`, `Print Preview`, `Save`, `New`a `Zoom`. Pokud takový objekt byl vložen do kontejneru, který podporuje `IOleCommandTarget`, může objekt povolit jeho tlačítka a přeposlání příkazů do kontejneru ke zpracování, když na ně uživatel klikne. Pokud kontejner chtěl vloženému objektu vytisknout sám sebe, mohl by vytvořit tento požadavek odesláním příkazu prostřednictvím rozhraní `IOleCommandTarget` vloženého objektu.

`IOleCommandTarget` je rozhraní podobné automatizaci, které je používáno klientem k vyvolání metod na serveru. Nicméně použití `IOleCommandTarget` ukládá režijní náklady na volání prostřednictvím rozhraní automatizace, protože programátory nemusejí používat obvykle nákladnou `Invoke` metodu `IDispatch`.

V prostředí MFC používají `IOleCommandTarget` rozhraní servery pro aktivní dokumenty, aby mohly kontejnery aktivních dokumentů odesílat příkazy na server. Třída serveru aktivního dokumentu `CDocObjectServerItem`používá mapy rozhraní MFC (viz [TN038: MFC/OLE IUnknown Implementation](../mfc/tn038-mfc-ole-iunknown-implementation.md)) k implementaci rozhraní `IOleCommandTarget`.

`IOleCommandTarget` je také implementována ve třídě `COleFrameHook`. `COleFrameHook` je nedokumentovaná třída knihovny MFC, která implementuje funkce okna rámce místních editačních kontejnerů. `COleFrameHook` používá také mapy rozhraní MFC k implementaci rozhraní `IOleCommandTarget`. `COleFrameHook`implementace `IOleCommandTarget` předávají příkazy OLE do `COleDocObjectItem`kontejnerů aktivních dokumentů odvozený od sebe. To umožňuje, aby kontejner aktivních dokumentů knihovny MFC přijímal zprávy z obsažených serverů aktivních dokumentů.

## <a name="mfc-ole-command-maps"></a>Mapy příkazů technologie OLE v MFC

Vývojáři knihovny MFC mohou využít výhod `IOleCommandTarget` pomocí map příkazů technologie OLE knihovny MFC. Mapy příkazů OLE jsou jako mapy zpráv, protože je lze použít pro mapování příkazů OLE na členské funkce třídy, která obsahuje mapu příkazů. Chcete-li tuto práci provést, umístěte makra do mapy příkazů a určete skupinu příkazů OLE příkazu, který chcete zpracovat, příkaz OLE a ID příkazu [WM_COMMANDové](/windows/win32/menurc/wm-command) zprávy, která bude odeslána při přijetí příkazu OLE. MFC také poskytuje řadu předdefinovaných maker pro standardní příkazy OLE. Seznam standardních příkazů OLE, které byly původně určeny pro použití s aplikacemi systém Microsoft Office, najdete v tématu výčet OLECMDID, který je definován v docobj. h.

Když aplikace MFC obdrží příkaz OLE, který obsahuje mapu příkazů OLE, knihovna MFC se pokusí najít ID příkazu a skupinu příkazů pro požadovaný příkaz v mapě příkazů OLE aplikace. Pokud se najde shoda, WM_COMMAND zpráva se odešle do aplikace obsahující mapu příkazů s ID požadovaného příkazu. (Podívejte se na popis `ON_OLECMD` níže.) Tímto způsobem jsou příkazy OLE odesílané do aplikace přeměněny na WM_COMMAND zprávy pomocí knihovny MFC. Zprávy WM_COMMAND jsou poté směrovány prostřednictvím mapy zpráv aplikace pomocí architektury [směrování příkazů](../mfc/command-routing.md) standardu MFC.

Na rozdíl od map zpráv nejsou službou ClassWizard podporovány mapy příkazů technologie OLE knihovny MFC. Vývojáři knihovny MFC musí přidat položku Podpora mapování příkazů OLE a položky mapování příkazů OLE ručně. Mapy příkazů OLE lze přidat do serverů knihovny MFC aktivního dokumentu v libovolné třídě, která je ve WM_COMMANDm řetězu zpráv, v době, kdy aktivní dokument je aktivní v kontejneru. Tyto třídy zahrnují třídy aplikace odvozené od [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [objektu CDocument](../mfc/reference/cdocument-class.md)a [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). V kontejnerech aktivních dokumentů lze mapy příkazů OLE přidat pouze do třídy odvozené od [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md). V kontejnerech aktivního dokumentu budou také zprávy WM_COMMAND odesílány pouze do mapy zpráv v třídě odvozené od `COleDocObjectItem`.

## <a name="ole-command-map-macros"></a>Makra mapování příkazů OLE

Použijte následující makra pro přidání funkce mapy příkazů do třídy:

```cpp
DECLARE_OLECMD_MAP ()
```

Toto makro přechází do deklarace třídy (obvykle v hlavičkovém souboru) třídy, která obsahuje mapu příkazů.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
Název třídy, která obsahuje mapu příkazů.

*baseClass*<br/>
Název základní třídy třídy, která obsahuje mapu příkazů

Toto makro označuje začátek mapy příkazů. Použijte toto makro v implementačním souboru pro třídu, která obsahuje mapu příkazů.

```
END_OLECMD_MAP()
```

Toto makro označuje konec mapy příkazů. Použijte toto makro v implementačním souboru pro třídu, která obsahuje mapu příkazů. Toto makro musí vždy následovat po BEGIN_OLECMD_MAPm makru.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Ukazatel na identifikátor GUID skupiny příkazů příkazu OLE. Tento parametr má pro standardní skupinu příkazů OLE **hodnotu null** .

*olecmdid*<br/>
ID příkazu OLE příkazu, který má být vyvolán.

*id*<br/>
ID zprávy WM_COMMAND, která se má odeslat do aplikace obsahující mapu příkazů při vyvolání tohoto příkazu OLE

Pomocí makra ON_OLECMD v mapě příkazů přidejte položky pro příkazy OLE, které chcete zpracovat. Po přijetí příkazů OLE budou převedeny na určenou zprávu WM_COMMAND a směrována přes mapu zpráv aplikace pomocí standardní architektury MFC příkazů pro směrování.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat schopnost zpracování příkazů OLE do serveru knihovny MFC aktivního dokumentu pro zpracování příkazu [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) OLE. V tomto příkladu se předpokládá, že jste použili AppWizard k vygenerování aplikace MFC, která je aktivní dokumentový server.

1. V souboru hlaviček odvozené třídy `CView`přidejte do deklarace třídy makro DECLARE_OLECMD_MAP.

    > [!NOTE]
    > Použijte třídu odvozenou od `CView`, protože se jedná o jednu ze tříd na aktivním Dokumentovém serveru, která je v řetězci směrování WM_COMMAND zpráv.

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

2. Do implementačního souboru pro třídu odvozenou od `CView`přidejte makra BEGIN_OLECMD_MAP a END_OLECMD_MAP:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Pokud chcete zpracovat standardní příkaz pro tisk OLE, přidejte do mapy příkazů makro [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) , které určuje ID příkazu OLE pro standardní tiskový příkaz a **ID_FILE_PRINT** pro ID WM_COMMAND. **ID_FILE_PRINT** je standardní ID příkazu pro tisk používané aplikacemi MFC generovanými v AppWizard:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Všimněte si, že jedno ze standardních příkazů OLE, které jsou definovány v AfxDocOb. h, lze použít místo makra ON_OLECMD, protože **OLECMDID_PRINT** je standardní ID příkazu OLE. Makro ON_OLECMD_PRINT provede stejnou úlohu jako ON_OLECMD makro zobrazené výše.

Když aplikace typu kontejner odešle tomuto serveru **OLECMDID_PRINT** příkaz prostřednictvím rozhraní `IOleCommandTarget` serveru, obslužná rutina příkazu pro tisk v knihovně MFC bude vyvolána na serveru, což způsobí, že Server vytiskne aplikaci. Kód kontejneru aktivního dokumentu k vyvolání tiskového příkazu, který byl přidán do výše uvedeného postupu, by vypadal přibližně takto:

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

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
