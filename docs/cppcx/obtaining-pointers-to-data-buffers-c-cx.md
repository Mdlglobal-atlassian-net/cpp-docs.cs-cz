---
title: Získání ukazatelů do vyrovnávací paměti dat (C++/CX)
ms.date: 11/19/2018
ms.assetid: db4f9370-dd95-4896-b5b8-4b202284f579
ms.openlocfilehash: 9e60adc4163e96349f6f4bafa919944e5d8d5b51
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032366"
---
# <a name="obtaining-pointers-to-data-buffers-ccx"></a>Získání ukazatelů do vyrovnávací paměti dat (C++/CX)

V modulu Windows Runtime poskytuje rozhraní [Windows::Storage::Streams::IBuffer](/uwp/api/windows.storage.streams.ibuffer) pro přístup k datovým vyrovnávacím bodům jazykově neutrální prostředky založené na datovém proudu. V jazyce C++ můžete získat nezpracovaný ukazatel základního bajtového pole pomocí rozhraní IBufferByteAccess knihovny prostředí Windows Runtime, které je definováno v souboru robuffer.h. Pomocí tohoto přístupu můžete upravit bajtpole na místě bez vytváření zbytečných kopií dat.

Následující diagram znázorňuje obrazový prvek XAML, jehož zdrojem je [windows::UI::Xaml::Media::Imaging WriteableBitmap](/uwp/api/windows.ui.xaml.media.imaging.writeablebitmap). Klientská aplikace, která je napsaná v `WriteableBitmap` libovolném jazyce, může předat odkaz na kód Jazyka C++ a pak c++ můžete použít odkaz získat na základní vyrovnávací paměti. V aplikaci univerzální platformy Windows, která je napsána v jazyce C++, můžete funkci v následujícím příkladu použít přímo ve zdrojovém kódu bez jeho zabalení do součásti prostředí Windows Runtime.

![C&#43;&#43; kód, který přistupuje k datům pixelů přímo](../cppcx/media/ibufferbyteaccessdiagram.png "C&#43;&#43; kód, který přistupuje k datům pixelů přímo")

## <a name="getpointertopixeldata"></a>GetPointerToPixelData

Následující metoda přijímá [systém Windows::Storage::Streams::IBuffer](/uwp/api/windows.storage.streams.ibuffer) a vrací nezpracovaný ukazatel do základního pole bajtů. Chcete-li volat funkci, předejte vlastnost [WriteableBitmap::PixelBuffer.](/uwp/api/windows.ui.xaml.media.imaging.writeablebitmap.pixelbuffer)

```cpp
#include <wrl.h>
#include <robuffer.h>
using namespace Windows::Storage::Streams;
using namespace Microsoft::WRL;
typedef uint8 byte;
// Retrieves the raw pixel data from the provided IBuffer object.
// Warning: The lifetime of the returned buffer is controlled by
// the lifetime of the buffer object that's passed to this method.
// When the buffer has been released, the pointer becomes invalid
// and must not be used.
byte* Class1::GetPointerToPixelData(IBuffer^ pixelBuffer, unsigned int *length)
{
    if (length != nullptr)
    {
        *length = pixelBuffer ->Length;
    }
    // Query the IBufferByteAccess interface.
    ComPtr<IBufferByteAccess> bufferByteAccess;
    reinterpret_cast<IInspectable*>( pixelBuffer)->QueryInterface(IID_PPV_ARGS(&bufferByteAccess));

    // Retrieve the buffer data.
    byte* pixels = nullptr;
    bufferByteAccess->Buffer(&pixels);
    return pixels;
}
```

## <a name="complete-example"></a>Kompletní příklad

Následující kroky ukazují, jak vytvořit aplikaci c# `WriteableBitmap` univerzální platformy Windows, která předává dll součásti Prostředí Pro prostředí Windows++ systému Windows Runtime. Kód Jazyka C++ získá ukazatel na vyrovnávací paměť obrazového bodu a provede jednoduchou úpravu na místě v obraze. Jako alternativu můžete vytvořit klientskou aplikaci v jazyce Visual Basic, JavaScript nebo C++ místo Jazyka C#. Pokud používáte C++, nepotřebujete dll komponenty; tyto metody můžete přidat přímo do třídy MainPage nebo do jiné třídy, kterou definujete.

#### <a name="create-the-client"></a>Vytvoření klienta

1. Šablona projektu blank aplikace slouží k vytvoření aplikace C# Universal Windows Platform.

1. V souboru MainPage.xaml

   - Pomocí tohoto xaml `Grid` nahradit prvek:

        ```xml
        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <StackPanel HorizontalAlignment="Left" Margin="176,110,0,0" VerticalAlignment="Top" Width="932">
                <Image x:Name="Pic"/>
                <Button Content="Process Image" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Height="47" Click="Button_Click_1"/>
            </StackPanel>
        </Grid>
        ```

1. V MainPage.xaml.cs

   1. Přidejte tyto deklarace oboru názvů:

        ```csharp
        using Windows.Storage;
        using Windows.Storage.FileProperties;
        using Windows.UI.Xaml.Media.Imaging;
        using Windows.Storage.Streams;
        using Windows.Storage.Pickers;
        ```

   1. Přidejte `WriteableBitmap` do třídy `MainPage` proměnnou `m_bm`člena a pojmenujte ji .

        ```csharp
        private WriteableBitmap m_bm;
        ```

   1. Použijte následující kód nahradit `OnNavigatedTo` metodu se zakázaným inzerováním. Tím se při spuštění aplikace otevře výběr souborů. (Všimněte `async` si, že klíčové slovo je přidán do podpisu funkce).

        ```csharp
        async protected override void OnNavigatedTo(NavigationEventArgs e)
        {
            FileOpenPicker openPicker = new FileOpenPicker();
            openPicker.ViewMode = PickerViewMode.Thumbnail;
            openPicker.SuggestedStartLocation = PickerLocationId.PicturesLibrary;
            openPicker.FileTypeFilter.Add(".jpg");
            openPicker.FileTypeFilter.Add(".jpeg");
            openPicker.FileTypeFilter.Add(".png");

            StorageFile file = await openPicker.PickSingleFileAsync();
            if (file != null)
            {
                // Get the size of the image for the WriteableBitmap constructor.
                ImageProperties props = await file.Properties.GetImagePropertiesAsync();
                m_bm = new WriteableBitmap((int)props.Height, (int)props.Width);
                m_bm.SetSource(await file.OpenReadAsync());
                Pic.Source = m_bm;
            }
            else
            {
                //  Handle error...
            }
        }
        ```

   1. Přidejte obslužnou rutinu události pro tlačítko. (Vzhledem `ImageManipCPP` k tomu, že odkaz na obor názvů ještě nebyl vytvořen, může mít v okně editoru podtržení vlnovkou.)

        ```csharp
        async private void Button_Click_1(object sender, RoutedEventArgs e)
        {
            ImageManipCPP.Class1 obj = new ImageManipCPP.Class1();
            await obj.Negativize(m_bm);
            Pic.Source = m_bm;
        }
        ```

#### <a name="create-the-c-component"></a>Vytvoření komponenty C++

1. Přidejte novou komponentu prostředí Windows Runtime systému `ImageManipCPP`C++ do existujícího řešení a pojmenujte ji . Přidejte odkaz na něj v projektu C# kliknutím pravým tlačítkem myši na tento projekt v **Průzkumníku řešení** a výběrem **add**, **reference**.

1. Ve třídě1.h

   1. Přidejte `typedef` to na druhý `#pragma once`řádek, těsně po :

        ```cpp
        typedef uint8 byte;
        ```

   1. Přidejte `WebHostHidden` atribut těsně nad `Class1` začátek deklarace.

        ```cpp
        [Windows::Foundation::Metadata::WebHostHidden]
        ```

   1. Přidat podpis této `Class1`veřejné metody do :

        ```cpp
        Windows::Foundation::IAsyncAction^ Negativize(Windows::UI::Xaml::Media::Imaging::WriteableBitmap^ bm);
        ```

   1. Přidejte podpis `GetPointerToPixelData` z metody, která je zobrazena v předchozím fragmentu kódu. Ujistěte se, že tato metoda je soukromá.

1. Ve třídě 1.cpp

   1. Přidejte `#include` tyto direktivy a deklarace oboru názvů:

        ```cpp
        #include <ppltasks.h>
        #include <wrl.h>
        #include <robuffer.h>

        using namespace Windows::Storage;
        using namespace Windows::UI::Xaml::Media::Imaging;
        using namespace Windows::Storage::Streams;
        using namespace Microsoft::WRL;
        ```

   1. Přidejte implementaci `GetPointerToPixelData` z předchozího fragmentu kódu.

   1. Přidejte implementaci `Negativize`. Tato metoda vytvoří efekt, který se podobá filmu negativní obrácením hodnoty každé hodnoty RGB v obrazovém bodu. Metodu provedeme asynchronní, protože na větších obrázcích může trvat znatelné množství času na dokončení.

        ```cpp
        IAsyncAction^ Class1::Negativize(WriteableBitmap^ bm)
        {
            unsigned int length;
            byte* sourcePixels = GetPointerToPixelData(bm->PixelBuffer, &length);
            const unsigned int width = bm->PixelWidth;
            const unsigned int height = bm->PixelHeight;

            return create_async([this, width, height, sourcePixels]
            {
                byte* temp = sourcePixels;
                for(unsigned int k = 0; k < height; k++)
                {
                    for (unsigned int i = 0; i < (width * 4); i += 4)
                    {
                        int pos = k * (width * 4) + (i);
                        temp[pos] = ~temp[pos];
                        temp[pos + 1] = ~temp[pos + 1] / 3;
                        temp[pos + 2] = ~temp[pos + 2] / 2;
                        temp[pos + 3] = ~temp[pos + 3];
                    }
                }
            });

        }
        ```

      > [!NOTE]
      > Tato metoda může běžet rychleji, pokud používáte AMP nebo paralelní vzorky knihovny paralelizovat operace.

1. Ujistěte se, že máte ve složce obrázky alespoň jeden obrázek, a stisknutím klávesy F5 program zkompilujte a spusťte.
