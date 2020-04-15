---
title: Třída CDumpContext
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: aa549e5347bf2bd357fa3c28e81a0309ea4f4aff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374009"
---
# <a name="cdumpcontext-class"></a>Třída CDumpContext

Podporuje datový proud orientovaný diagnostický výstup ve formě textu čitelného pro člověka.

## <a name="syntax"></a>Syntaxe

```
class CDumpContext
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Vytvoří `CDumpContext` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Vypíše uvedenou položku v šestnáctkovém formátu.|
|[CDumpContext::Flush](#flush)|Vyprázdní všechna data ve vyrovnávací paměti kontextu výpisu.|
|[CDumpContext::GetDepth](#getdepth)|Získá celé číslo odpovídající hloubce výpisu.|
|[CDumpContext::HexDump](#hexdump)|Zazdá bajty obsažené v poli v šestnáctkovém formátu.|
|[CDumpContext::Hloubka nastavení](#setdepth)|Nastaví hloubku výpisu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CDumpContext::operátor&lt;&lt;](#operator_lt_lt)|Vloží proměnné a objekty do kontextu výpisu.|

## <a name="remarks"></a>Poznámky

`CDumpContext`nemá základní třídu.

Můžete použít [afxDump](diagnostic-services.md#afxdump), `CDumpContext` předdeclared objekt, pro většinu vašeho dumpingu. Objekt `afxDump` je k dispozici pouze v ladicí verzi knihovny tříd Microsoft Foundation.

Několik [diagnostických služeb](../../mfc/reference/diagnostic-services.md) `afxDump` paměti používá pro svůj výstup.

V prostředí systému Windows je `afxDump` výstup z předdefinovaného `cerr` objektu, koncepčně podobný datovému `OutputDebugString`proudu, směrován do ladicího programu prostřednictvím funkce systému Windows .

Třída `CDumpContext` má přetížené vkládání ( **<<**) `CObject` operátor pro ukazatele, které vypisuje data objektu. Pokud potřebujete vlastní formát výpisu pro odvozený objekt, přepište [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Většina tříd Microsoft Foundation `Dump` implementuje potlačenou člennou funkci.

Třídy, které nejsou `CObject`odvozeny `CString` `CTime`od `CTimeSpan`, například , `CDumpContext` a , mají své vlastní přetížené `CFileStatus`vkládání `CPoint`operátory, stejně jako často používané struktury, jako jsou , , a `CRect`.

Pokud použijete [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) nebo [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makro v implementaci `CObject::Dump` vaší třídy, `CObject`vytiskne název vaší odvozené třídy. V opačném případě `CObject`se vytiskne .

Třída `CDumpContext` je k dispozici s ladicí a release verze `Dump` knihovny, ale členská funkce je definována pouze v ladicí verzi. Pomocí **příkazů #ifdef _DEBUG**  /  `#endif` můžete vytvořit závorku diagnostického kódu, včetně vlastních `Dump` členských funkcí.

Před vytvořením `CDumpContext` vlastního objektu `CFile` je nutné vytvořit objekt, který slouží jako cíl výpisu.

Další informace `CDumpContext`naleznete v tématu [Ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDumpContext`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext::CDumpContext

Vytvoří objekt třídy `CDumpContext`.

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parametry

*pSoubor*<br/>
Ukazatel na `CFile` objekt, který je cíl výpisu.

### <a name="remarks"></a>Poznámky

Objekt `afxDump` je vytvořen automaticky.

Nezapisovat `CFile` do podkladového, když je aktivní kontext výpisu; v opačném případě budete zasahovat do skládky. V prostředí systému Windows je výstup směrován do ladicího programu prostřednictvím funkce `OutputDebugString`systému Windows .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::DumpAsHex

Zapíše zadaný typ formátovaný jako šestnáctková čísla.

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CDumpContext` objekt.

### <a name="remarks"></a>Poznámky

Volání této členské funkce vypisovat položku zadaného typu jako šestnáctkové číslo. Chcete-li vyřadit pole, zavolejte [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext::Flush

Vynutí všechna zbývající data ve vyrovnávacích pamětnicích, které mají být zapsány do souboru připojeného k kontextu výpisu stavu.

```
void Flush();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext::GetDepth

Určuje, zda je zpracováván hluboký nebo mělký výpis.

```
int GetDepth() const;
```

### <a name="return-value"></a>Návratová hodnota

Hloubka výpisu, jak `SetDepth`je nastavena .

### <a name="example"></a>Příklad

  Viz příklad pro [SetDepth](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext::HexDump

Vypíše pole bajtů formátovaných jako šestnáctková čísla.

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parametry

*lpszLine*<br/>
Řetězec pro výstup na začátku nového řádku.

*pby*<br/>
Ukazatel na vyrovnávací paměť obsahující bajty, které mají být uloženy.

*nBajtu bajtů*<br/>
Počet bajtů, které mají být uloženy.

*nŠířka*<br/>
Maximální počet bajtů vynechaných na řádek (nikoli šířka výstupního řádku).

### <a name="remarks"></a>Poznámky

Chcete-li vyřadit jeden konkrétní typ položky jako šestnáctkové číslo, zavolejte [CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::operátor&lt;&lt;

Výstupy zadaných dat do kontextu výpisu.

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz. `CDumpContext` Pomocí vrácené hodnoty můžete zapsat více vložení na jeden řádek zdrojového kódu.

### <a name="remarks"></a>Poznámky

Operátor vložení je přetížený `CObject` pro ukazatele i pro většinu primitivních typů. Ukazatel na znak má za následek výpis obsahu řetězce; ukazatel **void** má za následek šestnáctkový výpis adresy pouze. Longlong výsledkem výpis u 64bitové podepsané celé číslo; ULONGLONG výsledky výpisu 64bitové nepodepsané celé číslo.

Pokud použijete IMPLEMENT_DYNAMIC nebo IMPLEMENT_SERIAL makro v implementaci vaší třídy, `CObject::Dump`vytiskne operátor `CObject`vložení , a vytiskne název vaší odvozené třídy. V opačném případě `CObject`se vytiskne . Pokud přepíšete `Dump` funkci třídy, můžete poskytnout smysluplnější výstup obsahu objektu namísto šestnáctkového výpisu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext::Hloubka nastavení

Nastaví hloubku pro výpis.

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parametry

*nNová hloubka*<br/>
Nová hodnota hloubky.

### <a name="remarks"></a>Poznámky

Pokud vypouštíte primitivní `CObject` typ nebo jednoduchý, který neobsahuje žádné ukazatele na jiné objekty, je dostatečná hodnota 0. Hodnota větší než 0 určuje hluboký výpis, kde jsou všechny objekty vypovězeny rekurzivně. Například hluboký výpis kolekce vypíše všechny prvky kolekce. V odvozených třídách můžete použít jiné specifické hodnoty hloubky.

> [!NOTE]
> Cyklické odkazy nejsou zjištěny v hluboké výpisy a může mít za následek nekonečné smyčky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
