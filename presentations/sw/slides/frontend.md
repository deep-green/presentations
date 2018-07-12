class: center, middle
# Frontend - Unreal Engine

---

## Technologien
### Frontend - Unreal Engine
- Unreal Engine Version 4.19.2
- SocketIO Plugin für Unreal v0.8.0
- Visual Studio 2017

---

## C++ Code Beispiel
### Frontend - Unreal Engine
- Login Widget
- Funktionen sind über die Blueprint aufrufbar

```c++
UCLASS()
class DEEPGREEN_API ULoginWidget : public UUserWidget
{
	GENERATED_BODY()
	
	public:
	UFUNCTION(BlueprintCallable, Category = "Login")
		static int checkCredentials(FString name, FString password, FString token);

	UFUNCTION(BlueprintCallable, Category = "Register")
		static int registerAccount(FString name, FString password, FString email);
		static int getGuestAccount();
	
	
};
```

---

## Unreal Engine Blueprints
### Frontend - Unreal Engine

- Weiß -> Programmablauf
- Gelb -> Vektoren
- Türkis -> Integer
- Hell-grün -> Float
- Rot -> Boolean
- Pink -> String
- Blau -> Objekte

---
## FEN String Konvertierung
### Frontend - Unreal Engine
<img src="images/frontend/FENtoArray.PNG" width="100%" />

---
## FEN String zu Array
### Frontend - Unreal Engine
<img src="images/frontend/FENtoArray1.PNG" width="100%" />

---
## FEN String leere Felder
### Frontend - Unreal Engine
<img src="images/frontend/FENtoArray2.PNG" width="100%" />

---
## FEN String Figuren
### Frontend - Unreal Engine
<img src="images/frontend/FENtoArray3.PNG" width="100%" />


