# TwowayviewModel
kotlinproject
package com.lovely.kotlinproject

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.databinding.DataBindingUtil
import androidx.lifecycle.ViewModelProvider
import com.lovely.kotlinproject.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
    private lateinit var binding:ActivityMainBinding
    private lateinit var viewModel:TwoWayDBviewModel
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
       binding=DataBindingUtil.setContentView(this,R.layout.activity_main)
       viewModel=ViewModelProvider(this)[TwoWayDBviewModel::class.java]
        binding.myViewModel=viewModel
        binding.lifecycleOwner=this
    }
}
#TwoWayDBviewModel.kt
package com.lovely.kotlinproject

import androidx.lifecycle.MutableLiveData
import androidx.lifecycle.ViewModel

class TwoWayDBviewModel:ViewModel() {
    var name : MutableLiveData<String> = MutableLiveData<String>()
    init {
        name.value="Android Studio"
    }
}
#Main.xml
<?xml version="1.0" encoding="utf-8"?>
<layout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools">
    <data>
        <variable
            name="myViewModel"
            type="com.lovely.kotlinproject.TwoWayDBviewModel" />
    </data>
<androidx.constraintlayout.widget.ConstraintLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint=""
        android:id="@+id/et_input"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:text="@={myViewModel.name}"
        />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/tv_display"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        android:text="@={myViewModel.name}"/>
    

</androidx.constraintlayout.widget.ConstraintLayout>
</layout>
