TOPOG_TOOL = ./create_topog_refinedSampling.py
TOPOG_SRC  = --source_file /archive/gold/datasets/topography/GEBCO_2020/GEBCO_2020.nc --source_lon lon --source_lat lat --source_elv elevation

TARGS = ocean_topog_res0.125_Merc.nc \
	ocean_topog_res0.125_SO.nc \
	ocean_topog_res0.125_SC.nc \
	ocean_topog_res0.125_BP.nc \

all: $(TARGS) hash.md5
	cat hash.md5
	md5sum -c hash.md5

test: $(TARGS)
	cat hash.md5
	md5sum -c hash.md5
	make clean
#Note: --no_changing_meta arg is used to avoid putting time/platform dependent info in the files so that they can  be checksumed.
#      Please do not use this arg for normal grid generation, it prevents adding useful information to meta data.
ocean_topog_res0.125_SO.nc:
	time $(TOPOG_TOOL) --hgridfilename /work/Niki.Zadeh/MOM6-examples_myfork/ice_ocean_SIS2/OM4_0125/preprocessing_test/ocean_hgrid.ncSO.nc --outputfilename $(@F) $(TOPOG_SRC) --no_changing_meta

ocean_topog_res0.125_SC.nc:
	time $(TOPOG_TOOL) --hgridfilename /work/Niki.Zadeh/MOM6-examples_myfork/ice_ocean_SIS2/OM4_0125/preprocessing_test/ocean_hgrid.ncSC.nc --outputfilename $(@F) $(TOPOG_SRC) --no_changing_meta

ocean_topog_res0.125_Merc.nc:
	time $(TOPOG_TOOL) --hgridfilename /work/Niki.Zadeh/MOM6-examples_myfork/ice_ocean_SIS2/OM4_0125/preprocessing_test/ocean_hgrid.ncMerc.nc --outputfilename $(@F) $(TOPOG_SRC) --no_changing_meta

ocean_topog_res0.125_BP.nc:
	time $(TOPOG_TOOL) --hgridfilename /work/Niki.Zadeh/MOM6-examples_myfork/ice_ocean_SIS2/OM4_0125/preprocessing_test/ocean_hgrid.ncBP.nc --outputfilename $(@F) $(TOPOG_SRC) --no_changing_meta


hash.md5: | $(TARGS)
	md5sum $(TARGS) > $@
	cat $@

check:
	md5sum -c hash.md5

clean:
	rm -f $(TARGS) $(DEPS) ocean_topog_res*.nc
