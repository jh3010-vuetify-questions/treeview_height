<template>
    <v-container class="green lighten-5" fluid>
      <v-row no-gutters dense style="flex-wrap: nowrap" class="align-stretch primary lighten-3">
          <v-col class="flex-grow-0 flex-shrink-0" style="flex-basis: 20em;">
              <v-card flat class="green lighten-3" style="height: 100%;">

                  Some Column Context<br>
                  Some Column Context<br>
                  Some Column Context<br>
                  Some Column Context<br>
                  Some Column Context<br>
                  Some Column Context<br>
                  Some Column Context<br>

              </v-card>
          </v-col>
          <v-col class="flex-grow-2" style="background-color: red;">

            <v-tabs
                v-model="tab"
                background-color="primary lighten-3"
                id = "contentView"
            >

                <v-tab
                    v-for="tabName in tabNames"
                    :key="tabName.id"
                    :href="`#${tabName}`"
                >

                    {{ tabName }}

                </v-tab>

                <v-tab-item
                    v-for="tabName in tabNames"
                    :key="tabName.id"
                    :value="`${tabName}`"
                    class="yellow lighten-4"
                    style="height: 100%"
                >

                    <v-container fluid>
                        <v-row dense col no-gutters>
                            <v-col cols = "12">
                                <v-treeview dense activatable :items="childrenForTab">
                                    <template v-slot:label="{ item }">
                                        <span>{{ item.name }}</span>
                                    </template>
                                </v-treeview>
                            </v-col>
                        </v-row>
                    </v-container>

                </v-tab-item>

            </v-tabs>

          </v-col>
      </v-row>
    </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data()
    {
        return {
        tabNames: [ 'a', 'b' ],
        tab: null,
        }
    },

    computed:
    {
        childrenForTab()
        {
            if ( this.tab == 'a' )
            {
                return [
                { name: '1' },
                { name: '2' },
                { name: '3' },
                { name: '4' }
                ]
            }
            else
            {
                return [
                    { name: '1' }
                ]
            }
        }
    }
}
</script>

<style scoped>

#contentView {
  height: 100%;
  display: flex;
  flex-direction: column;
}

.v-window.v-item-group {
  flex-grow: 1;
}

.v-window__container {
  height: 100%;
}

</style>