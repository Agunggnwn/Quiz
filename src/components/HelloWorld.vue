<template>
  <div class="hello">
    <h1>Selamat Mengerjakan</h1>

    <p :style="'color: red'" v-if="poin < items.length-((items.length*3)/10)">Maaf, Anda Belum Bisa Menjadi Siswa SMKN 4 Bandung</p>
    <p :style="'color: green'" v-else>Selamat, Anda Berhak Masuk SMKN 4 Bandung </p>
    <p>{{ 'Poin Anda '+poin}}</p>

    <div v-for="(item,index) in items" :key="item.pertanyaan" :options="item.pertanyaan">
      <p>{{index+1}}. {{ item.pertanyaan}}</p>
      <div  v-for="pilih in item.pilihan" :key="pilih.pilihan" :options="pilih.pilihan">
        <input type="radio"  :name="'name'+index"
         @click="checkJawaban(index,pilih.pilihan)"
        :value="pilih.pilihan" >{{ pilih.pilihan }}
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'HelloWorld',
  data: function(){
    return {
      show: true,
      poin:0,
      jawabanbenar: [],
      items:[
      {
        name:'soal1',
        pertanyaan: 'Kepanjangan NATO ?',
        answer:String,
        check:true,
        pilihan:[
        { pilihan:'North Atlantic Treaty Organization' },
        { pilihan:'North Asia Treaty Organization' },
        { pilihan:'North Asean Treaty Organization'},
        { pilihan:'Semua jawaban benar' } ],
        jawaban:'North Atlantic Treaty Organization'
      },
      {
        pertanyaan: 'Aku adalah seorang ..... Mempunyai pedang panjang . Isi yang tepat adalah',
        name:'soal2',
        check:true,
        answer:String,
        pilihan:[
        { pilihan:'Kapiten' },
        { pilihan:'anak gembala' },
        { pilihan:'Pilot' },
        { pilihan:'Preman' }
        ],
        jawaban:'Kapiten'
      },
      {
        pertanyaan: 'Presiden Indonesia Saat ini ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Jokowi' },
        { pilihan:'Ridwan Kamil' },
        { pilihan:'Ir.Soekarno' },
        { pilihan:'Soeharto' }
        ],
        jawaban:'Jokowi'
      },
      {
        pertanyaan: 'Siapa guru PWD kita ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'Pa Taopik' },
        { pilihan:'Pa Ferry' },
        { pilihan:'Pa Lukman' },
        { pilihan:'Bu Arne' }
        ],
        jawaban:'Pa Ferry'
      },
      {
        pertanyaan: 'Indonesia Merdeka Pada tahun ?',
        answer:String,
        check:true,
        name:'soal3',
        pilihan:[
        { pilihan:'1944' },
        { pilihan:'1945' },
        { pilihan:'1954' },
        { pilihan:'1955' }
        ],
        jawaban:'1945'
      }
      ]
    }
  },
  methods: {
    checkJawaban(i,jawab){

      if(this.items[i].jawaban === jawab){
        if(this.jawabanbenar.indexOf(i) == -1){
          this.poin++;
          this.jawabanbenar.push(i);
        }
      }
      if(this.items[i].jawaban !== jawab){
        if(this.jawabanbenar.indexOf(i) != -1){
          this.poin--;
          this.jawabanbenar.splice(this.jawabanbenar.indexOf(i), 1);
        }
      }

        this.items[i].check = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
