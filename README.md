## Issue application

This application can be used to showcase issues, bugs and crashes in specific libraries.

At the moment it showcases [issue with popping child nav graph](https://issuetracker.google.com/issues/249988437) (with parameters) and safe args.

#### Issue 249988437

Steps: 
1) Navigate from FirstFragment to Child nav graph (with non-nullable parameters).
2) Navigate to ThirdFragment using SafeArgs and the app crashes.

Crash log:

```
Process: cz.dels.issues, PID: 1743
java.lang.NullPointerException: null cannot be cast to non-null type kotlin.Long
at androidx.navigation.NavType$Companion$LongType$1.get(NavType.kt:352)
at androidx.navigation.NavType$Companion$LongType$1.get(NavType.kt:342)
at androidx.navigation.NavArgument.verify(NavArgument.kt:76)
at androidx.navigation.NavDestination.addInDefaultArgs(NavDestination.kt:502)
at androidx.navigation.NavController.addEntryToBackStack(NavController.kt:1865)
at androidx.navigation.NavController.addEntryToBackStack$default(NavController.kt:1813)
at androidx.navigation.NavController$navigate$4.invoke(NavController.kt:1721)
at androidx.navigation.NavController$navigate$4.invoke(NavController.kt:1719)
at androidx.navigation.NavController$NavControllerNavigatorState.push(NavController.kt:287)
at androidx.navigation.fragment.FragmentNavigator.navigate(FragmentNavigator.kt:246)
at androidx.navigation.fragment.FragmentNavigator.navigate(FragmentNavigator.kt:162)
at androidx.navigation.NavController.navigateInternal(NavController.kt:260)
at androidx.navigation.NavController.navigate(NavController.kt:1719)
at androidx.navigation.NavController.navigate(NavController.kt:1545)
at androidx.navigation.NavController.navigate(NavController.kt:1472)
at androidx.navigation.NavController.navigate(NavController.kt:1930)
at cz.dels.issues.SecondFragment.onViewCreated$lambda-0(SecondFragment.kt:38)
at cz.dels.issues.SecondFragment.$r8$lambda$XDYnOS_cYrafiNQ5rcCu1WCn0IE(Unknown Source:0)
at cz.dels.issues.SecondFragment$$ExternalSyntheticLambda0.onClick(Unknown Source:2)
```

Note: If in step 2 SaveArgs is not used then navigation works correctly.