---
title: Agregace a makra vytváření tříd
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 554210ab0a26bc54a716a389a1660c4cbd42a209
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168654"
---
# <a name="aggregation-and-class-factory-macros"></a>Agregace a makra vytváření tříd

Tato makra poskytují způsoby řízení agregace a deklaraci tříd factory třídy.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, že váš objekt může být agregovaný (výchozí).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje objekt pro vytváření tříd, který bude [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), výchozí objekt pro vytváření tříd knihovny ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje objekt factory vaší třídy jako objekt pro vytváření tříd.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako objekt pro vytváření tříd.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako objekt pro vytváření tříd.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje virtuální `GetControllingUnknown` funkci.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, že objekt nelze agregovat.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, že váš objekt musí být agregovaný.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Kontroluje hodnotu vnějšího neznámého objektu a deklaruje vaše objekty, které jsou v případě potřeby agregovatelné nebo neagregovatelné.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Chrání vnější objekt před odstraněním během vytváření vnitřního objektu.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Určuje příznaky VIEWSTATUS kontejneru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Určuje, že váš objekt může být agregovaný.

```cpp
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy, kterou definujete jako agregovatelné.

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje toto makro k určení výchozího agregačního modelu. Chcete-li tuto výchozí hodnotu přepsat, zadejte do definice třídy buď makro [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) , nebo [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako objekt pro vytváření tříd.

```cpp
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) používá toto makro k deklaraci výchozího objektu pro vytváření tříd pro váš objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>CComClassFactory – třída

Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

```cpp
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Poznámky

`CComClassFactory`implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , které obsahuje metody pro vytvoření objektu KONKRÉTNÍho identifikátoru CLSID, a také uzamykání objektu pro vytváření tříd v paměti, aby bylo možné rychle vytvořit nové objekty. `IClassFactory`je nutné implementovat pro každou třídu, kterou zaregistrujete do systémového registru a ke kterému přiřadíte CLSID.

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory)makra, který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete-li přepsat toto výchozí nastavení, zadejte jedno z DECLARE_CLASSFACTORY*xxx* makra v definici třídy. Například makro [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) používá určenou třídu pro objekt pro vytváření tříd:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Definice výše uvedené třídy určuje, `CMyClassFactory` který se použije jako výchozí objekt pro vytváření tříd. `CMyClassFactory`musí odvozovat `CComClassFactory` od a `CreateInstance`přepsat.

Knihovna ATL poskytuje tři další makra, která deklaruje objekt pro vytváření tříd:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Používá [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), které řídí vytváření prostřednictvím licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Používá [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), který vytváří objekty ve více objektech Apartment.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Používá [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), který vytvoří jeden objekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Deklaruje jako `cf` objekt pro vytváření tříd.

```cpp
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parametry

*CF*<br/>
pro Název třídy, která implementuje objekt factory vaší třídy.

### <a name="remarks"></a>Poznámky

Parametr *CF* se musí odvozovat z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a přepsat `CreateInstance` metodu.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje makro [DECLARE_CLASSFACTORY](#declare_classfactory) , které určuje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY_EX do definice třídy vašeho objektu, přepíšete tuto výchozí hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako objekt pro vytváření tříd.

```cpp
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parametry

*LIC*<br/>
pro Třída, která implementuje `VerifyLicenseKey`, `GetLicenseKey`a `IsLicenseValid`.

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje makro [DECLARE_CLASSFACTORY](#declare_classfactory) , které určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY2 do definice třídy vašeho objektu, přepíšete tuto výchozí hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>CComClassFactory2 – třída

Tato třída implementuje rozhraní [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

```cpp
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parametry

*průkaz*<br/>
Třída, která implementuje následující statické funkce:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Poznámky

`CComClassFactory2`implementuje rozhraní [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , což je rozšíření [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`řídí vytváření objektů pomocí licence. Objekt pro vytváření tříd, který je spuštěn na licencovaném počítači, může poskytnout licenční klíč za běhu. Tento licenční klíč umožňuje aplikaci vytvářet instance objektů, pokud není k dispozici úplná licence na počítač.

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje [DECLARE_CLASSFACTORY](#declare_classfactory)makra, který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete- `CComClassFactory2`li použít, zadejte [DECLARE_CLASSFACTORY2](#declare_classfactory2) makro v definici třídy vašeho objektu. Příklad:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, parametr `CComClassFactory2`šablony do, musí implementovat statické funkce `VerifyLicenseKey`, `GetLicenseKey`a. `IsLicenseValid` Následuje příklad jednoduché třídy licence:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`je odvozen z obou `CComClassFactory2Base` i *licencí*. `CComClassFactory2Base`, zase, je odvozen z `IClassFactory2` a **CComObjectRootEx\< CComGlobalsThreadModel >**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd.

```cpp
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje makro [DECLARE_CLASSFACTORY](#declare_classfactory) , které určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY_AUTO_THREAD do definice třídy vašeho objektu, přepíšete tuto výchozí hodnotu.

Když vytváříte objekty ve více objektech Apartment (na serveru mimo proc), přidejte DECLARE_CLASSFACTORY_AUTO_THREAD do vaší třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>CComClassFactoryAutoThread – třída

Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) a umožňuje vytvářet objekty ve více objektech Apartment.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```cpp
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Poznámky

`CComClassFactoryAutoThread`je podobný jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umožňuje vytvářet objekty ve více objektech Apartment. Chcete-li využít výhod této podpory, odvodit modul EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída obsahuje [DECLARE_CLASSFACTORY](#declare_classfactory)makra, který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Chcete- `CComClassFactoryAutoThread`li použít, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) makro v definici třídy vašeho objektu. Příklad:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako objekt pro vytváření tříd.

```cpp
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parametry

*objektu*<br/>
pro Název vašeho objektu třídy.

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zahrnuje makro [DECLARE_CLASSFACTORY](#declare_classfactory) , které určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí objekt pro vytváření tříd. Nicméně zahrnutím makra DECLARE_CLASSFACTORY_SINGLETON do definice třídy vašeho objektu, přepíšete tuto výchozí hodnotu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>CComClassFactorySingleton – třída

Tato třída je odvozena z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

```cpp
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída.

`CComClassFactorySingleton`je odvozen z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metody jednoduše dotazuje tento objekt na ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

Objekty ATL normálně získávají objekt pro vytváření tříd odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory)makra, který deklaruje `CComClassFactory` jako výchozí objekt pro vytváření tříd. Chcete- `CComClassFactorySingleton`li použít, zadejte [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) makro v definici třídy vašeho objektu. Příklad:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Deklaruje virtuální funkci `GetControllingUnknown`.

```cpp
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Poznámky

Pokud se zobrazí chybová zpráva kompilátoru, která není definována (například in `GetControllingUnknown` `CComAggregateCreator`), přidejte toto makro do objektu.

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Určuje, že objekt nelze agregovat.

```cpp
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název objektu třídy, který definujete jako neagregovatelné.

### <a name="remarks"></a>Poznámky

DECLARE_NOT_AGGREGATABLE způsobí `CreateInstance` vrácení chyby (CLASS_E_NOAGGREGATION), pokud je proveden pokus o agregaci do objektu.

Ve výchozím nastavení obsahuje [CComCoClass](../../atl/reference/ccomcoclass-class.md) makro [DECLARE_AGGREGATABLE](#declare_aggregatable) , které určuje, že váš objekt lze agregovat. Chcete-li přepsat toto výchozí chování, zahrňte DECLARE_NOT_AGGREGATABLE do definice třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Určuje, že váš objekt musí být agregovaný.

```cpp
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název objektu třídy, který definujete jako agregovatelné.

### <a name="remarks"></a>Poznámky

DECLARE_ONLY_AGGREGATABLE způsobí chybu (E_FAIL), pokud je proveden pokus o provedení `CoCreate` objektu jako neagregovaný objekt.

Ve výchozím nastavení obsahuje [CComCoClass](../../atl/reference/ccomcoclass-class.md) makro [DECLARE_AGGREGATABLE](#declare_aggregatable) , které určuje, že váš objekt lze agregovat. Chcete-li přepsat toto výchozí chování, zahrňte DECLARE_ONLY_AGGREGATABLE do definice třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Určuje, že instance třídy **CComPolyObject \< ** *x* **>** je vytvořena při vytvoření objektu.

```cpp
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název objektu třídy, který definujete jako agregovatelné nebo neagregovatelné.

### <a name="remarks"></a>Poznámky

Při vytváření se kontroluje hodnota vnějšího neznámého. Pokud je NULL, `IUnknown` je implementován pro neagregovaný objekt. Pokud není vnější neznámá hodnota NULL, `IUnknown` je implementována pro agregovaný objekt.

Výhodou použití DECLARE_POLY_AGGREGATABLE je, abyste se vyhnuli `CComAggObject` tomu `CComObject` , aby a ve vašem modulu zpracovával agregované a neagregované případy. Jeden `CComPolyObject` objekt zpracovává oba případy. To znamená, že ve vašem modulu existují jenom jednu kopii vtable a jednu kopii funkcí. Pokud je tabulka vtable velká, může to podstatně snížit velikost modulu. Pokud je však tabulka vtable malá, použití `CComPolyObject` může mít za následek mírně větší velikost modulu, protože není optimalizována pro agregované nebo neagregované objekty, jako jsou `CComAggObject` a. `CComObject`

Makro DECLARE_POLY_AGGREGATABLE je automaticky deklarováno v objektu, pokud použijete Průvodce ovládacím prvkem ATL k vytvoření úplného ovládacího prvku.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Chrání váš objekt před smazáním, pokud (během [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) vnitřní agregovaný objekt zvýší počet odkazů a pak sníží počet na 0.

```cpp
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Toto makro umístěte do třídy ovládacího prvku ActiveX knihovny ATL a určete tak příznaky VIEWSTATUS kontejneru.

```cpp
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parametry

*statusFlags*<br/>
pro Příznaky VIEWSTATUS Seznam příznaků naleznete v tématu [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
