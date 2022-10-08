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
