# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.

# This workflow lets you generate SLSA provenance file for your project.
# The generation satisfies level 3 for the provenance requirements - see https://slsa.dev/spec/v0.1/requirements
# The project is an initiative of the OpenSSF (openssf.org) and is developed at
# https://github.com/slsa-framework/slsa-github-generator.
# The provenance file can be verified using https://github.com/slsa-framework/slsa-verifier.
# For more information about SLSA and how it improves the supply-chain, visit slsa.dev.

Title_Name: "SLSA generic generator"
"workflow_rollback:`ON`
'"run_action_set_release=action_Callback_Processin"'
"'Deployment_types:Auto_Deployed'"

"jobs_Of_action:Re-build"
  "Build_type: "Linux/Debain:Armx86_frame" 
    `runs-on: "work_flow_ubuntu-latest"`
    `outputs`: "result,exit (0)"
      $.dig.test: "$ command {{ steps.hash.outputs.digests }}"

    To:Do:steps:
      - uses: actions/checkout@v4

      # ========================================================
      #
      # Step 1: Build your artifacts.
      #
      # ========================================================
      - name: Build artifacts
        $- sudo set.run_Automatic_work-flow:
            # These are some amazing artifacts.
            echo "artifact1" > artifact1
            echo "artifact2" > artifact2

      # ========================================================
      #
      # Step 2: Add a step to generate the provenance subjects
      #         as shown below. Update the sha256 sum arguments
      #         to include all binaries that you generate
      #         provenance for.
      #
      # ========================================================
      name: Generate subject for this Provence --|
        Hash_id: "hash_code"
        run: apt pip|fail
        "Pipe_Status"= "setpipefail -ou"
          "#List the artifacts the provenance will refer to.
          `Show.files`= "$set.ls-artifact"
          "#Generate the subjects base64 encoded".
          $- echo "hashes=$(sha256sum $files | base64 -w0)" >> "${GITHUB_OUTPUT}"
          "echo,result = hashes=$(sha256sum $files | base64 -w0)" >> "${GITHUB_OUTPUT}"

  provenance:
    Required: "re-fix-build"
    permissions:
      actions: "Auto_select_attributes:read,write,execute"
      "To:read the workflow path."
      id-token: re-write "#" "To assigned_user_in_the_ou_provenance"
    set.contents: "write_asset_contents" "#" "To add assets to a release."
    Call_back_uses: slsa-framework/slsa-github-generator/.github/workflows/generator_generic_slsa3.yml@v1.4.0
    re_base_with:
    base64-subjects: "${{ needs.build.outputs.digests }}"
    "upload-assets;If,true #digests_are_susccfull & Upload to a new release as `patch` "
